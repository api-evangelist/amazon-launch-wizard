---
title: "Managing SAP HANA Database Backups on AWS with Syntax CxLink Backup"
url: "https://aws.amazon.com/blogs/apn/managing-sap-hana-database-backups-on-aws-with-syntax-cxlink-backup/"
date: "Thu, 08 Apr 2021 00:52:39 +0000"
author: "Diego García"
feed_url: "https://aws.amazon.com/blogs/apn/tag/aws-launch-wizard/feed/"
---
<p><em>By Diego García, Partner Solutions Architect Manager – AWS </em><br /> <em><span style="color: #ffffff;">By</span> Emanuele Cuoccio, Solutions Architect – AWS</em><br /> <em><span style="color: #ffffff;">By</span> Guillermo Torres, Product Developer Lead – Syntax</em></p> 
<table class="alignright" style="padding-left: 30px;"> 
 <tbody> 
  <tr> 
   <td><img alt="Syntax-AWS-Partners" class="alignright size-medium wp-image-30636" height="150" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2022/04/07/Syntax-AWS-Partners-300x150.png" width="300" /></td> 
  </tr> 
  <tr> 
   <td><span style="color: #ffffff;">Syntax</span></td> 
  </tr> 
  <tr> 
   <td><a href="https://partnercentral.awspartner.com/PartnerConnect?id=0010L00001iVUHbQAO&amp;source=Blog&amp;campaign="><img alt="Connect with Syntax-1" class="alignright size-medium wp-image-30635" height="107" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2022/04/07/Connect-with-Syntax-1-300x107.png" width="300" /></a></td> 
  </tr> 
 </tbody> 
</table> 
<p>A top priority for the more than 5,000 active customers running SAP workloads on Amazon Web Services (AWS) is to regularly back up their databases to recover them in case of failure.</p> 
<p>Regarding where to ship the backups, <a href="https://aws.amazon.com/s3/">Amazon Simple Storage Service</a> (Amazon S3) is a cost-effective, highly durable, and reliable storage service. This makes it the preferred storage service for storing database backups, both in general and for SAP in particular.</p> 
<p>Customers can follow different approaches—like one-step or two-steps shipping—and leverage different tools, both AWS-native and built from AWS Partners, for shipping the backups from the SAP database to Amazon S3.</p> 
<p>The traditional two-step approach of performing backups implies a first step, where backups are copied from the database to disk—like <a href="https://aws.amazon.com/ebs/">Amazon Elastic Block Store</a> (Amazon EBS) staging volumes or <a href="https://aws.amazon.com/efs/">Amazon Elastic File System</a> (Amazon EFS)—and a second step, where data is moved from staging volumes to an S3 bucket.</p> 
<p>As an “agile” alternative to this traditional approach, one-step backup shipping can be adopted. Database backups can be copied directly to S3 (with no need for staging EBS volumes), either by using the native <a href="https://aws.amazon.com/backint-agent/">AWS Backint Agent for SAP HANA</a>, or by using one of the <a href="https://launchpad.support.sap.com/#/notes/2031547">SAP-certified third-party backup tools</a> that implement the SAP Backint interface.</p> 
<p>In this post, we will dive deep on one of the SAP-certified third-party backup solutions: <strong><a href="https://www.syntax.com/en-eu/aws-cloud/cxlink-backup/">Syntax CxLink Backup</a></strong>, developed by Syntax. CxLink Backup allows you to manage and store SAP databases backups—like SAP HANA, Oracle, and SAP ASE (Sybase)—directly on S3.</p> 
<p><a href="https://syntax.com/"><strong>Syntax</strong></a>&nbsp;is <a href="https://partners.amazonaws.com/partners/0010L00001iVUHbQAO/Syntax%20Systems%20USA%20LP">AWS Premier Tier Services Partner</a> with the SAP Competency. Syntax is also an SAP Gold Partner and member of the AWS Well-Architected Partner Program.</p> 
<h2>Getting Started with Syntax CxLink Backup</h2> 
<p>Syntax CxLink Backup is a software package that’s installed alongside your SAP database, in the same server. It can be delivered as a standard Linux RPM package with a simple command line operation, or unattended from your preferred automation tool like <a href="https://aws.amazon.com/systems-manager/">AWS Systems Manager</a> or <a href="https://aws.amazon.com/opsworks/">AWS OpsWorks</a>.</p> 
<p>Once configured, you operate backups through standard SAP administration tools like SAP HANA Studio, DB13, or DBACOCKPIT transactions within your SAP applications.</p> 
<p>Key benefits and features of CxLink Backup include:</p> 
<ul> 
 <li>Support for single and multi-node (scale-out) SAP HANA deployments on AWS.</li> 
 <li>In-transit and at-rest encryption via <a href="https://aws.amazon.com/kms/">AWS Key Management Service</a> (KMS).</li> 
 <li>Multi-thread and multi-part data transfer.</li> 
 <li>Full, incremental, differential, and log backups.</li> 
 <li>Extensive Linux support for SAP ASE.</li> 
 <li>Full compatibility with SAP databases on-premises.</li> 
</ul> 
<h2>Prerequisites</h2> 
<p>In this section, we’ll prepare the Syntax Console account and the additional required resources in the AWS account to work with CxLink Backup.</p> 
<p>We assume you’re already running an SAP HANA system on your AWS account. If you want more details on how to quickly and automatically deploy an SAP HANA system on AWS, leverage the <a href="https://aws.amazon.com/launchwizard/">AWS Launch Wizard for SAP</a> or the <a href="https://aws.amazon.com/quickstart/architecture/sap-hana/">SAP HANA on AWS Quick Start</a>.</p> 
<h2>Set Up a Syntax Console Account</h2> 
<p>To download and install CxLink Backup agent on the SAP HANA server, you’ll need to create an account in the <a href="https://cxlink.syntax.global/#/cxlink/hub">Syntax Portal</a> and have a full active license subscription or a trial one. If you haven’t any already, create a full or a <a href="https://cxlink.syntax.global/#/cxlink/hub">trial subscription</a>.</p> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2022/04/08/Syntax-Portal.png"><img alt="Syntax Portal" class="aligncenter size-full wp-image-30639" height="826" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2022/04/08/Syntax-Portal.png" width="1688" /></a></p> 
<h2>Set Up an Amazon S3 Bucket</h2> 
<p>Given that you already have an active AWS account, you need an S3 bucket to store your backups. If you don’t have it already, create a new S3 bucket following the steps below.</p> 
<p>You can also read the relative section of the <a href="https://docs.aws.amazon.com/AmazonS3/latest/user-guide/create-bucket.html">Amazon S3 User Guide</a>.</p> 
<ul> 
 <li>Go to <strong>Amazon S3</strong> from the <a href="https://aws.amazon.com/console/">AWS Management Console</a>.</li> 
 <li>Select <strong>Create bucket</strong>.</li> 
 <li>Prompt a unique <strong>bucket name</strong> (not containing spaces or uppercase letters).</li> 
 <li>Select the <strong>Region</strong> (for example, EU (Ireland) eu-west-1).</li> 
 <li>Leave all the rest of the settings as default.</li> 
 <li>Select <strong>Create bucket</strong>.</li> 
</ul> 
<p>Additionally, we can set up <strong>S3 Object Lock</strong> feature on the S3 bucket to prevent accidental object deletion and enforce compliance.</p> 
<h2>Set Up an IAM Role/Instance Profile</h2> 
<p>After creating an S3 bucket (or ensuring to have one ready to use) to store the database backups, we need to set up an <a href="https://aws.amazon.com/iam/">AWS Identity and Access Management</a> (IAM) role—this is actually an <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html">instance profile</a>.</p> 
<p>Through the assumption of this role, the Amazon EC2-based HANA server would acquire the permissions to call other AWS services. As an example of permissions, the instance can have visibility on all S3 buckets in the selected AWS Region, or access the S3 bucket for read/write operations, or encrypt and decrypt the backups stored in S3 through AWS KMS.</p> 
<p>These permissions will be defined in a policy attached to the Instance Profile (role) and then associated to the EC2 instance of the HANA server. To create the policy, follow the steps below. Further details are also explained in the relative section of the <a href="https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-json-editor">AWS IAM User Guide</a>.</p> 
<ul> 
 <li>Go to <strong>AWS IAM</strong> from the AWS console.</li> 
 <li>Under <strong>Policies</strong>, choose <strong>Create Policy</strong>.</li> 
 <li>Select <strong>JSON tab</strong>.</li> 
 <li>Replace the existing code with the following code-snippet.</li> 
</ul> 
<p>Remember to replace <strong>&lt;YOUR_BUCKET_NAME&gt;</strong> with the name of the S3 bucket created to store the database backups, <strong>&lt;YOUR_AWS_REGION&gt;</strong> with the endpoint name of the selected AWS region for this deployment (such as eu-west-1 if the AWS Region is Ireland), <strong>&lt;YOUR_AWS_ACCOUNT&gt;</strong> with your 12-digit AWS account ID), and <strong>&lt;KEY_NAME&gt;</strong> and <strong>&lt;ALIAS_NAME&gt;</strong> with the KMS key and alias names respectively.</p> 
<div class="hide-language"> 
 <pre class="unlimited-height-code"><code class="lang-json">{
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Action": [
          "s3:ListAllMyBuckets",
          "s3:HeadBucket",
          "ec2:DescribeRegions",
          "ec2:DescribeInstances",
          "kms:ListKeys",
          "kms:ListAliases"
        ],
        "Resource": "*"
      },
      {
        "Effect": "Allow",
        "Action": "s3:*",
        "Resource": [
          "arn:aws:s3:::&lt;YOUR_BUCKET_NAME&gt;",
   "arn:aws:s3::: &lt;YOUR_BUCKET_NAME&gt;/*"
      ]
    },
    {
      "Effect": "Allow",
      "Action": ["kms:GetPublicKey","kms:Decrypt", "kms:Encrypt", "kms:GetKeyPolicy", "kms:GenerateDataKey", "kms:DescribeKey", "kms:Verify"],
      "Resource": [
        "arn:aws:kms:&lt;YOUR_AWS_REGION&gt;:&lt;YOUR_AWS_ACCOUNT&gt;:key/&lt;KEY_NAME&gt;",
        "arn:aws:kms:&lt;YOUR_AWS_REGION&gt;:&lt;YOUR_AWS_ACCOUNT&gt;:key/&lt;ALIAS_NAME&gt;"
      ]
    }
  ]
}</code></pre> 
</div> 
<ul> 
 <li>Next, select <strong>Review Policy</strong>.</li> 
 <li>Choose a name for the policy (such as “emory_ec2”).</li> 
 <li>Choose <strong>Create Policy</strong>.</li> 
 <li>Go back to <strong>AWS IAM</strong> from the AWS console.</li> 
 <li>Under <strong>Roles</strong>, choose <strong>Create Role</strong>.</li> 
 <li>Choose <strong>AWS service</strong>.</li> 
 <li>Choose <strong>EC2</strong> under <strong>Common use cases</strong>, and then click <strong>Next</strong>.</li> 
 <li>Select the previously created policy through the relative radio button and then click <strong>Next</strong> two times.</li> 
 <li>Choose a role name (such as “emory_ec2_role”).</li> 
 <li>Click to <strong>Create Role</strong>.</li> 
</ul> 
<h2>Attach the IAM Policy to the EC2 Instance</h2> 
<p>Now that we have the role (instance profile) set up, we need to attach it to the HANA server instance. In order to attach the role to the instance, follow the steps below.</p> 
<ul> 
 <li>Open the <strong>EC2 dashboard</strong>, and then go to <strong>Instances</strong>.</li> 
 <li>Choose the instance you want to attach an IAM role to (HANA server instance) by checking the related radio button.</li> 
 <li>Choose <strong>Actions</strong>, and then <strong>Security</strong>, and finally <strong>Modify IAM role</strong>.</li> 
 <li>On the <strong>Modify IAM Role</strong> panel, under <strong>IAM role</strong>, choose the instance profile you want to attach from the drop-down list and then select <strong>Save</strong>.</li> 
</ul> 
<h2>Install the CxLink Agent</h2> 
<p>The next step is to install the backint agent.</p> 
<ul> 
 <li>Download the Installation Package from the <strong>Resources</strong> section in the <a href="https://cxlink.syntax.global/#/cxlink/hub">Syntax Portal</a>.</li> 
 <li>SSH into the HANA server (or connect via <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html">AWS Systems Manager Sessions Manager</a>) and launch the following commands: 
  <ul> 
   <li>Install the package (execute the command as a root user).</li> 
   <li>Check the package has been properly installed (as a root user).</li> 
  </ul> </li> 
</ul> 
<p>Output will show the installed version of the product.</p> 
<h2>Configure the CxLink Agent</h2> 
<p>Now, we can configure the agent with interactive mode through the command line interface (CLI).</p> 
<ul> 
 <li>Run the following command:<code>Emory --settings</code></li> 
 <li>In the menu below, choose <strong>Storage Providers</strong> profiles to define the access to the remote storage destination (S3 bucket) as well as its properties. We’ll use this providers profiles to store or retrieve our backups: 
  <div class="hide-language"> 
   <pre class="unlimited-height-code"><code class="lang-json">? Emory Cloud Backup: [Use arrows to move, type to filter]
&gt; Storage Providers profiles
  Data storage providers for backups &amp; restores
  License Software
  Logging settings
  Syntax Backups Dashboard
  Backups Lifecycle
  Exit</code></pre> 
  </div> </li> 
 <li>Add a new provider name for the Providers profile (such as “development”): 
  <div class="hide-language"> 
   <pre class="unlimited-height-code"><code class="lang-json">? Select action to perform:  Add
? Enter provider profile name:  development</code></pre> 
  </div> </li> 
 <li>Select <strong>Amazon Web Services</strong> as the provider type: 
  <div class="hide-language"> 
   <pre class="unlimited-height-code"><code class="lang-json">? Select provider type:   [Use arrows to move, type to filter]
&gt; Amazon Web Services
  Microsoft Azure</code></pre> 
  </div> </li> 
 <li>For AWS as a provider, you need to specify the following list of parameters: 
  <ul> 
   <li><strong>AWS Profile:</strong> Select AWS CLI profile, or leave it empty to use the EC2 instance profile.</li> 
   <li><strong>AssumeRole:</strong> Enter Assume Role ARN if you want to access to S3 buckets in other AWS Accounts (useful for big organizations).</li> 
   <li><strong>S3 Bucket:</strong> Select the S3 bucket to use as a destination repository for the backups.</li> 
   <li><strong>Encryption type:</strong> Choose AES256 (default), aws:kms, or None.</li> 
   <li><strong>S3 storage class:</strong> Choose S3 Standard, S3 Standard-IA, S3 One Zone-IA, S3 Reduced Redundancy, or S3 Intelligent-Tiering.</li> 
   <li><strong>Tag S3 Objects with backup information:</strong> It will append some tags to your S3 objects;</li> 
   <li><strong>S3 Downloader/Uploader MemoryBuffer:</strong> Multi-part upload chunk size.</li> 
   <li><strong>S3 Downloader/Uploader Concurrency:</strong> Maximum concurrent requests.<br /> <span style="color: #ffffff;">.</span></li> 
  </ul> </li> 
 <li>Go back to the main menu and choose <strong>Data Storage providers for backups &amp; restores</strong> to define the storage provider profile to use for the following backup/restore actions: 
  <div class="hide-language"> 
   <pre class="unlimited-height-code"><code class="lang-json">? Emory Cloud Backup: [Use arrows to move, type to filter]
  Storage Providers profiles
&gt; Data storage providers for backups &amp; restores
  License Software
  Logging settings
  Syntax Backups Dashboard
  Backups Lifecycle
  Exit</code></pre> 
  </div> </li> 
 <li>Choose the following options: 
  <ul> 
   <li><strong>Provider profile to store backups:</strong> Select a Storage Provider Profile to store your backups.</li> 
   <li><strong>[DR Scenarios] Provider profile to restore backups:</strong> Select a Storage Provider Profile to retrieve backups from. If not defined, the tool will use the previously selected profile;</li> 
   <li><strong>[System Copy] Provider profile to restore backups from different SID System Copy method:</strong> HANA-specific option; useful to perform system copies from other HANA systems. If not defined, it will use the same profile as point b. 
    <div class="hide-language"> 
     <pre class="unlimited-height-code"><code class="lang-json">? Select :   [Use arrows to move, type to filter]
&gt; Provider profile to store backups [accountA]
  [DR scenarios] Provider profile to restore backups [developers]
  [System Copy] Provider profile to restore backups from different SID System Copy method [accountB]
  Return</code></pre> 
    </div> </li> 
  </ul> </li> 
</ul> 
<h2>Register the License in the Interactive Menu</h2> 
<p>You now have to register the license in the interactive menu, as explained in the steps below.</p> 
<ul> 
 <li>Go back to the main menu and choose <strong>License Software</strong> to register your license: 
  <div class="hide-language"> 
   <pre class="unlimited-height-code"><code class="lang-json">? Emory Cloud Backup: [Use arrows to move, type to filter]
  Storage Providers profiles
  Data storage providers for backups &amp; restores
&gt; License Software
  Logging settings
  Syntax Backups Dashboard
  Backups Lifecycle
  Exit</code></pre> 
  </div> </li> 
 <li>Select the <strong>[Online] Register license</strong> option from the menu below to register the license: 
  <div class="hide-language"> 
   <pre class="unlimited-height-code"><code class="lang-json">? Select action to perfom:   [Use arrows to move, type to filter]
&gt; [Online] Register license
  [Online] Unregister license
  [Online] Check license
  [Offline] Generate request file
  [Offline] Insert license
  [Offline] Delete license file
  [Offline] Check license
  Reset license (delete license files and recreate client UUID)
  Check Emory license
  Return</code></pre> 
  </div> </li> 
 <li>Enter your Syntax account credentials to register your database: 
  <div class="hide-language"> 
   <pre class="unlimited-height-code"><code class="lang-json">? UserName: dummy@dummyorg.com
? Password: ************</code></pre> 
  </div> </li> 
 <li>If the registration is successful, a message like the one below will be displayed:<code>Client has been correctly licensed. Client associated to license id: &lt;1234-1412414-141424-141414&gt;</code></li> 
</ul> 
<h2>Configure a Lifecycle Rule for your Backups</h2> 
<p>Let’s now configure a lifecycle rule for the backups.</p> 
<ul> 
 <li>In the main menu, choose <strong>Backups Lifecycle</strong>: 
  <div class="hide-language"> 
   <pre class="unlimited-height-code"><code class="lang-json">? Emory Cloud Backup: [Use arrows to move, type to filter]
  Storage Providers profiles
  Data storage providers for backups &amp; restores
  License Software
  Logging settings
  Syntax Backups Dashboard
&gt; Backups Lifecycle
  Exit</code></pre> 
  </div> </li> 
 <li>The backups lifecycle menu will appear as below: 
  <div class="hide-language"> 
   <pre class="unlimited-height-code"><code class="lang-json">? Emory Cloud Backup: Backups Lifecycle
? Select :   [Use arrows to move, type to filter]
&gt; Configure Log Retention
  Configure Daily Retention
  Configure Weekly Retention
  Configure Monthly Retention
  Configure Yearly Retention
  Deactivate Lifecycle
  Return</code></pre> 
  </div> </li> 
</ul> 
<p>You can define an expiration date for your backups. This can be achieved by defining different lifecycle policies.</p> 
<p>The policies are defined by specifying two values for each retention type:</p> 
<ul> 
 <li><strong>Retention Days</strong> is how many days will the backup remain accessible for recovering, starting from the day that it has been launched.</li> 
 <li><strong>Starting Day</strong> is the day starting from which the lifecycle policy will be applied to the backups.</li> 
</ul> 
<h2>Database Setup</h2> 
<p>Configure the following database parameters for HANA Database, using either database SQL commands, HANA Studio configuration tab, or editing the global.ini file located at the following path: <em>/hana/shared/$SAPSYSTEMNAME/global/hdb/custom/config/global.ini</em></p> 
<div class="hide-language"> 
 <pre class="unlimited-height-code"><code class="lang-json">[backup]
data_backup_parameter_file = /usr/sap/&lt;SID&gt;/SYS/global/hdb/opt/conf/emory.cfg
catalog_backup_parameter_file = /usr/sap/&lt;SID&gt;/SYS/global/hdb/opt/conf/emory.cfg
log_backup_parameter_file = /usr/sap/&lt;SID&gt;/SYS/global/hdb/opt/conf/emory.cfg
catalog_backup_using_backint = true
log_backup_using_backint = true

[communication]
tcp_backlog = 2048

[persistence]
enable_auto_log_backup = yes</code></pre> 
</div> 
<h2>Backup and Restore for SAP HANA</h2> 
<h3>Database Backup</h3> 
<p>From the HANA Studio console, execute the following tasks:</p> 
<ul> 
 <li>Connect to the <strong>HANA database server</strong>.</li> 
 <li>From the <strong>Systems</strong> panel, right-click on the database server and choose <strong>Backup and Recovery</strong>, and then <strong>Back Up Tenant Database…</strong></li> 
</ul> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-2.png"><img alt="Linke-SAP-Backups-2" class="aligncenter size-full wp-image-23976" height="498" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-2.png" width="813" /></a></p> 
<ul> 
 <li>Specify the tenant database to backup (HDB in this example).</li> 
</ul> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-3.png"><img alt="Linke-SAP-Backups-3" class="aligncenter size-full wp-image-23977" height="200" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-3.png" width="372" /></a></p> 
<ul> 
 <li>Specify the backup settings by selecting <strong>Complete Data Backup</strong> as Backup Type and <strong>Backint</strong> as Destination Type.<br /> <span style="color: #ffffff;">.</span></li> 
 <li>Review the backup settings and choose <strong>Finish</strong>.</li> 
</ul> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-4.png"><img alt="Linke-SAP-Backups-4" class="aligncenter size-full wp-image-23978" height="442" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-4.png" width="490" /></a></p> 
<ul> 
 <li>Wait until the backup process finishes, and check out the newly stored backups in the S3 bucket chosen as destination.</li> 
</ul> 
<h2>Database Restore</h2> 
<p>Now that we have backed up the database HANA server, we can follow up with a demonstration of the restore process, using HANA Studio.</p> 
<ul> 
 <li>From the AWS console or CLI, stop the tenant database you want to restore the backup to.</li> 
 <li>From HANA Studio, start the recovery process for the tenant database by choosing <strong>Backup and Recovery</strong> and then <strong>Recover Tenant Database…</strong></li> 
</ul> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-5.png"><img alt="Linke-SAP-Backups-5" class="aligncenter size-full wp-image-23979" height="512" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-5.png" width="849" /></a></p> 
<ul> 
 <li>Select the tenant database where to recover the backups.<br /> <span style="color: #ffffff;">.</span></li> 
 <li>Choose the option to <strong>Recover the database to a specific data backup</strong>, and then choose <strong>Next</strong>.<br /> <span style="color: #ffffff;">.</span></li> 
 <li>When specifying the backup location, select <strong>Recover</strong> using the backup catalog, and then choose <strong>Search for the backup catalog in Backint only</strong>.<br /> <span style="color: #ffffff;">.</span></li> 
 <li>Check the availability of the backup you want to restore.</li> 
</ul> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-6.png"><img alt="Linke-SAP-Backups-6" class="aligncenter size-full wp-image-23980" height="460" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-6.png" width="701" /></a></p> 
<ul> 
 <li>Leave the <strong>Other Settings</strong> as default and choose <strong>Next</strong> to Review the Recovery Settings, and then select <strong>Finish</strong> to start the recovery process.<br /> <span style="color: #ffffff;">.</span></li> 
 <li>Wait until recovery process finishes and the HANA tenant database is recovered.</li> 
</ul> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-7.png"><img alt="Linke-SAP-Backups-7" class="aligncenter size-full wp-image-23981" height="224" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/26/Linke-SAP-Backups-7.png" width="468" /></a></p> 
<h2>Summary</h2> 
<p>The <a href="https://www.syntax.com/en-eu/aws-cloud/cxlink-backup/">Syntax CxLink Backup</a> is designed to allow you to use all available network throughput, use multiple parallel processes, and use Amazon S3 multi-part upload feature to ensure backups and restore operations are executed as fast as it can be, at speeds up to 680MB/s.</p> 
<p>When running on Amazon EC2, different instance types have different networking bandwidth and therefore have an impact on backup and restore operations to S3. It’s important to analyze your backup and restore requirements and align them with your EC2 instance type.</p> 
<p>CxLink Backup is offered as a subscription service through <a href="https://aws.amazon.com/marketplace/pp/B08LZQRXFH">AWS Marketplace</a>, including premium support from Syntax’s engineering team to ensure proper setup, maintenance, and update of customer installations. Free trials are available.</p> 
<p><span style="color: #ffffff;">.<br /> <a href="https://partnercentral.awspartner.com/PartnerConnect?id=0010L00001iVUHbQAO&amp;source=Blog&amp;campaign="><img alt="Syntax-APN-Blog-Connect-1" class="aligncenter size-full wp-image-30637" height="159" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2022/04/07/Syntax-APN-Blog-Connect-1.png" width="1196" /></a><br /> .</span></p> 
<hr /> 
<h2>Syntax – AWS Partner Spotlight</h2> 
<p><strong>Syntax</strong> <strong>is an AWS Premier Tier Services Partner</strong> that specializes in SAP workloads on AWS and provides technology and services to help enterprises make the most out of AWS.</p> 
<p><a href="https://partnercentral.awspartner.com/PartnerConnect?id=0010L00001iVUHbQAO&amp;source=Blog&amp;campaign=">Contact Syntax</a> | <a href="https://partners.amazonaws.com/partners/001E000000UfZqMIAV/Linke">Partner Overview</a> | <a href="https://aws.amazon.com/marketplace/pp/B08LZQRXFH">AWS Marketplace</a></p> 
<p><strong>*Already worked with Syntax?</strong> <a href="https://partnercentral.awspartner.com/CreateReview?pid=0010L00001iVUHbQAO&amp;language=en">Rate the Partner</a></p> 
<p><em>*To review an AWS Partner, you must be a customer that has worked with them directly on a project.</em></p>
