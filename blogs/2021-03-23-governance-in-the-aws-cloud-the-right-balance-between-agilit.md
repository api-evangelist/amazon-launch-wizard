---
title: "Governance in the AWS Cloud: The Right Balance Between Agility and Safety"
url: "https://aws.amazon.com/blogs/apn/governance-in-the-aws-cloud-the-right-balance-between-agility-and-safety/"
date: "Tue, 23 Mar 2021 16:57:52 +0000"
author: "Paolo Latella"
feed_url: "https://aws.amazon.com/blogs/apn/tag/aws-launch-wizard/feed/"
---
<p><em>By Paolo Latella, Cloud Practice Manager and APN Ambassador at Claranet Italia</em></p> 
<table class="alignright" style="padding-left: 30px;"> 
 <tbody> 
  <tr> 
   <td><a href="https://aws.amazon.com/partners/ambassadors/"><img alt="APN-Ambassadors-1" class="alignright size-medium wp-image-18087" height="150" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2020/07/10/APN-Ambassadors-1-300x150.jpg" width="300" /></a></td> 
  </tr> 
 </tbody> 
</table> 
<p>Cloud infrastructure provides more agility and responsiveness than traditional IT environments. This requires organizations to think differently about how they design, build, and manage applications.</p> 
<p>Cloud resources are disposable, and with a pay-per-use model it requires a strong integration between IT governance and organizational governance. Builders need to be able to operate in a cloud environment that’s agile and safe at the same time.</p> 
<p>In this post, I will introduce a decentralized model of cloud governance that can help you strike the right balance between agility and safety.</p> 
<p>As the Amazon Web Services (AWS) practice manager at Claranet Italia, I help customers move to the cloud while reducing the time between ideas and production. In the last few years, Claranet has helped many customers move their workloads to AWS, from scaled-up startups to enterprise organizations. During this journey, we push for a cloud-native approach and the right governance model.</p> 
<p>I am an Authorized Instructor Champion at AWS, and have been an <strong><a href="https://aws.amazon.com/partners/ambassadors/">APN Ambassador</a></strong> since 2018. APN Ambassadors work closely with AWS Solutions Architects to migrate, design, implement, and monitor AWS workloads.</p> 
<p><strong><a href="http://www.claranet.com/">Claranet</a></strong> is an <a href="https://partners.amazonaws.com/partners/001E000000ZLAC7IAP/Claranet%20Group">AWS Premier Consulting Partner</a> with AWS Competencies in DevOps, Migration, Data &amp; Analytics, and Digital Customer Experience. Claranet is also a member of the AWS Managed Service Provider (MSP) Partner Program.</p> 
<h2>Governance in the Cloud</h2> 
<p>Governance is a mix of processes, people, and technologies that drive the cloud journey. In my experience, the principles of cloud governance and challenges organizations face are as follows.</p> 
<p><strong>Principles:</strong></p> 
<ul> 
 <li>Drive cloud-native culture.</li> 
 <li>Align cloud strategy to business objectives and IT strategies.</li> 
 <li>Promote and leverage a <a href="https://aws.amazon.com/blogs/enterprise-strategy/using-a-cloud-center-of-excellence-ccoe-to-transform-the-entire-enterprise/">Cloud Center of Excellence</a> (CCoE).</li> 
 <li>Democratize emerging technologies.</li> 
</ul> 
<table class="alignright" style="padding-left: 30px;"> 
 <tbody> 
  <tr> 
   <td><img alt="Paolo Latella-APN-Ambassador-1" class="alignright size-full wp-image-23837" height="390" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Paolo-Latella-APN-Ambassador-1.png" width="281" /></td> 
  </tr> 
 </tbody> 
</table> 
<p><strong>Challenges:</strong></p> 
<ul> 
 <li>Identify the right KPI and ROI of cloud adoption.</li> 
 <li>Identify and maintain required policies and compliances.</li> 
 <li>Define (cloud-ready) contracts with internal and external stakeholders.</li> 
 <li>Support employees’ career paths with new skills.</li> 
 <li>Adapt the security and compliance process leveraging the <a href="https://aws.amazon.com/compliance/shared-responsibility-model/">Shared Responsibility Model</a>.</li> 
</ul> 
<p>Other challenges faced by organizations on a cloud journey include adapting risk evaluation and mitigation strategies; avoiding technology proliferation and pushing to build reusable, cloud-native components; and turning staff from skeptics to true believers.</p> 
<h2>Agility and Safety</h2> 
<p>One of the biggest challenges a governance team faces during cloud adoption is to improve the enterprise’s agility without compromising safety.</p> 
<p>Usually, the concept of cloud agility is quite clear, but safety often gets confused with cyber-security. In this post, I am using the term “safety” because it’s not only about (cyber) security.</p> 
<p>Security is the protection of our cloud environment from information disclosure or service disruption, while safety is more than this. Safety also refers to control on costs and resources configuration assessment.</p> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-Cloud-Governance-1.png"><img alt="Claranet-Cloud-Governance-1" class="aligncenter size-full wp-image-23829" height="301" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-Cloud-Governance-1.png" width="1041" /></a></p> 
<p style="text-align: center;"><em>Figure 1 – Cloud governance functions.</em></p> 
<p>To define the right balance between agility and safety, the cloud governance team must define new rules, engage the right people, and manage dynamic cloud resources leveraging <a href="https://aws.amazon.com/products/management-and-governance/">AWS Management and Governance services</a>.</p> 
<p>Most of the company resolves this problem by adopting a centralized governance (cloud resource broker). This approach guarantees maximum controls but reduces agility. We need to introduce a new concept of governance that’s more agile and based on DevOps principles and is therefore less centralized.</p> 
<p>In a decentralized governance model, it’s essential to develop a critical mass of people with AWS experience, establish new operational processes, and leverage services designed to improve agility and guarantee safety.</p> 
<p>The goal is to create a decentralized governance that permits great control over standards and costs (safety) while allowing better responsiveness to business needs (agility).</p> 
<h2>People and Process: The Cloud Center of Excellence</h2> 
<p>The right way to define and implement a decentralized model of governance is to bring together a group of cloud experts from within the organization to provide leadership, define best practices, and drive builders in cloud adoption.</p> 
<p>There are many ways to define a structure of Cloud Center of Excellence, but in each of these we can identify two entities:</p> 
<ul> 
 <li><strong>Functional CCoE:</strong> More related to provisioning and operating of the cloud resources.</li> 
 <li><strong>Advisor CCoE:</strong> More related to cloud strategies and impact on the business.</li> 
</ul> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-Cloud-Governance-2.png"><img alt="Claranet-Cloud-Governance-2" class="aligncenter size-full wp-image-23830" height="315" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-Cloud-Governance-2.png" width="474" /></a></p> 
<p style="text-align: center;"><em>Figure 2 – Structure of a Cloud Center of Excellence.</em></p> 
<p>The functional CCoE is an “elastic” component of the team because it scales and reorganize to meet the needs of the advisor CCoE and therefore of the business. The functional CCoE can be started with 2-3 people and grow up to include more team members.</p> 
<p>In any case, the functional CCoE is responsible for:</p> 
<ul> 
 <li>Defining best practices for design and operate applications in the cloud.</li> 
 <li>Providing centralized and shared services.</li> 
 <li>Creating reusable and preconfigured resources.</li> 
 <li>Implementing the right guardrails and related controls.</li> 
</ul> 
<p>With regards to best practices, the Cloud Center of Excellence creates and maintains design principles and architectural best practices for designing and running applications in the cloud.</p> 
<p>A good starting point is the <a href="https://aws.amazon.com/architecture/well-architected">AWS Well-Architected Framework</a>, which is based on a set of foundational questions that allow you to understand if a specific architecture aligns well with AWS best practices. The framework is built on five pillars: operational excellence, reliability, performance, security, and cost optimization.</p> 
<p>The CCoE must involve the builders during a definition of these new principles or practices (bottom-up approach). Also, when new processes have been defined or new technologies have been adopted, the CCoE should organize webinars, workshops, or more with goal to evangelize the rest of IT department.</p> 
<h2>Leveraging Shared Services and Templates</h2> 
<p>Use of shared services is one of the top architectural design principles. It permits builders to inherit standardized architecture during development of new services.</p> 
<p>The CCoE should push to create shared services to:</p> 
<ul> 
 <li>Separate the duties and responsibilities.</li> 
 <li>Centralize cross-projects services enabling a single point of control.</li> 
</ul> 
<p>For example, we can define <a href="https://docs.aws.amazon.com/solutions/latest/centralized-logging/architecture.html">centralized logging solutions</a> with the goal to collect, analyze, and display <a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html">Amazon CloudWatch Logs</a> of our spoke accounts in a single dashboard. Or, we can provide to our builders a <a href="https://aws.amazon.com/blogs/devops/cross-account-ci-cd-pipeline-single-tenant-saas/">cross-account CI/CD pipeline</a> to simplify and standardize tasks and introduce a separation of duties. Builders can develop and test the new release, but the deployment in production requires an authorization.</p> 
<p>The CCoE works with builders to produce company blueprints. These are reusable and preconfigured services that drive builders to adopt (reuse) a template reference on their projects. Inside the blueprints, we can find articles like those described on the <a href="https://aws.amazon.com/builders-library/">Amazon Builders’ Library</a>, or templates provided by <a href="https://aws.amazon.com/launchwizard/">AWS Launch Wizard</a>.</p> 
<p>The CCoE creates and manages catalogues of pre-approved cloud resources. This can range from a group of <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html">Amazon Machine Images</a> (AMIs) up to entire infrastructure.</p> 
<p>For creating and managing a catalogue of AMIs, one practice is to set up a process to <a href="https://aws.amazon.com/blogs/awsmarketplace/announcing-the-golden-ami-pipeline/">create golden AMIs using CI/CD pipeline</a> together with Chef and Packer, or use a managed service as <a href="https://docs.aws.amazon.com/imagebuilder/latest/userguide/what-is-image-builder.html">Amazon EC2 Image Builder</a>. For creating and managing entire infrastructures, we could use <a href="https://aws.amazon.com/cloudformation/">AWS CloudFormation</a> and <a href="https://aws.amazon.com/servicecatalog">AWS Service Catalog</a>, which allows us to have catalogues of pre-approved infrastructures.</p> 
<h2>Automate Everything</h2> 
<p>A decentralized model of governance works fine only if the CCoE simplifies the job of builders and allows the company to speed up the release of new products and services.</p> 
<p>When the business launches a new product or service, all the steps necessary to enable builders should be automated. From account creation (we use a multi-account environment for our projects) to the deployment of applications, all of the steps should be automated. Here, the degree of freedom can range all the way up to builders who are able to autonomously create cloud resources including the accounts.</p> 
<p>In any case, the Cloud Center of Excellence must define account provisioning process, enable controls on compliance and costs, and launch a pre-approved set of configurations (for example log centralization). These controls represents a perimeter that prevents builders from go off-road (guardrails).</p> 
<p>Using <a href="https://aws.amazon.com/controltower/">AWS Control Tower</a> or <a href="https://github.com/awslabs/aws-deployment-framework">AWS Deployment Framework</a> (ADF), the CCoE can set up and govern a multi-account AWS environment knowing accounts conform to best practices and that all defined guardrails are enabled.</p> 
<h2>Technologies: Controls Over Standards</h2> 
<p>To balance agility with safety, a decentralized model of governance requires a company govern its resources and monitor compliance across accounts. The Cloud Center of Excellence is responsible for defining and applying the right guardrails on accounts that developers create for their projects.</p> 
<p>Usually, these guardrails are implemented as controls, such as:</p> 
<ul> 
 <li><strong>Directive controls:</strong> Defines the guidance in design and build.</li> 
 <li><strong>Preventive controls:</strong> Protects workloads that prevent misconfiguration or vulnerabilities.</li> 
 <li><strong>Detective controls:</strong> Provides visibility and transparency over the operation.</li> 
 <li><strong>Responsive controls:</strong> Mitigates error or misconfiguration in real-time.</li> 
</ul> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-Cloud-Governance-3.png"><img alt="Claranet-Cloud-Governance-3" class="aligncenter size-full wp-image-23831" height="371" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-Cloud-Governance-3.png" width="844" /></a></p> 
<p style="text-align: center;"><em>Figure 3 – Safety vs. security.</em></p> 
<h3>Directive Controls</h3> 
<p>Directive controls are implemented as best practices and design principles. Here, the CCoE has a relevant role because it’s responsible for engaging and evangelizing builders about this directive. For example, the CCoE should communicate to builders the importance of using an <a href="https://aws.amazon.com/iam/#:~:text=AWS%20Identity%20and%20Access%20Management%20(IAM)%20enables%20you%20to%20manage,offered%20at%20no%20additional%20charge.">AWS Identity and Access Management</a> (IAM) role to delegate access to users, applications, or services.</p> 
<h3>Preventive Controls</h3> 
<p>Preventive controls are implemented as a set of policies at the account level or organization level. For account-level control, IAM provides user-based policies and resource-based policies that define what a builder can or can’t do on a specific account.</p> 
<p>For organization-level control, <a href="https://aws.amazon.com/organizations/">AWS Organizations</a> is a service that groups accounts in Organizational Units (OU) with the goal of defining the budgetary, security, and compliance needs on a specific group of accounts. For example, we can define three different OUs for every environment (development, pre-production, and production) and define three different preventive controls.</p> 
<p>For each OU, the CCoE can define one or more service control policies (SCPs) with the goal of creating the right guardrail for that account. For example, the CCoE can force the builders to apply a tag relate the cost center on <a href="https://aws.amazon.com/ec2/">Amazon Elastic Compute Cloud</a> (Amazon EC2) instances applying an SCP that require this tag to perform launch instance operation.</p> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-Cloud-Governance-4.png"><img alt="Claranet-Cloud-Governance-4" class="aligncenter size-full wp-image-23832" height="468" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-Cloud-Governance-4.png" width="1007" /></a></p> 
<p style="text-align: center;"><em>Figure 4 – SCP and identity policy.</em></p> 
<p>The configuration above is an example of the right balance between agility and safety. Builders have a policy that permits them to launch instances autonomously, but only if they follow the requirement (implemented by SCP) to put a tag on the instance. Remember, the SCP defined on AWS Organizations can be deployed automatically to a new account by AWS Control Tower.</p> 
<h3>Detective Controls</h3> 
<p>Detective controls are implemented as logs analysis or events processing. Usually, the output of a detective control is an alarm or metric on a dashboard.</p> 
<p>The task of the CCoE is to define standards on log format, push to centralize logging and events processing (the shared services), and obviously enable the log generation. The security pillar of AWS Well-Architected suggest the following best practices on these kind of controls:</p> 
<ul> 
 <li>Configure service and application logging.</li> 
 <li>Analyze logs, findings, and metrics centrally.</li> 
 <li>Automate response to events.</li> 
 <li>Implement actionable security events.</li> 
</ul> 
<p>With detective controls, <a href="https://aws.amazon.com/cloudtrail/">AWS CloudTrail</a> and <a href="https://aws.amazon.com/cloudwatch/">Amazon CloudWatch</a> can alert and act on operational or application issues. <a href="https://aws.amazon.com/premiumsupport/technology/trusted-advisor/">AWS Trusted Advisor</a> provide guidance on how you can optimize your infrastructure in terms of costs, performance, security and resilience.</p> 
<h3>Responsive Controls</h3> 
<p>Responsive controls process events from cloud resources with the goal of continuously auditing and assessing the overall compliance of AWS infrastructure. <a href="https://aws.amazon.com/config/">AWS Config</a> enables you to assess and evaluate the configurations of your AWS resources.</p> 
<p>With AWS Config rules, the CCoE can implement detective controls by processing events from resources and create real-time remediation actions using <a href="https://aws.amazon.com/systems-manager/">AWS Systems Manager</a> or <a href="https://aws.amazon.com/lambda/">AWS Lambda</a>. For example, you can implement a Config rule that assesses the configuration of security groups or bucket policy and fix it automatically in case of misconfiguration.</p> 
<p><a href="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-Cloud-Governance-5.png"><img alt="Claranet-Cloud-Governance-5" class="aligncenter size-full wp-image-23833" height="261" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-Cloud-Governance-5.png" width="981" /></a></p> 
<p style="text-align: center;"><em>Figure 5 – AWS Config rules in action.</em></p> 
<h2>Technologies: Controls Over Costs</h2> 
<p>Safety is also a budget and cost management issue. With agility in mind, we must allow builders to create new cloud resources without losing control of the costs.</p> 
<p>AWS provide several services to help you monitor costs:</p> 
<ul> 
 <li><a href="https://aws.amazon.com/aws-cost-management/aws-cost-explorer/">AWS Cost Explorer</a> enables you to view and analyze the costs and usage (detective control).</li> 
 <li><a href="https://aws.amazon.com/aws-cost-management/aws-budgets/">AWS Budgets</a> enables a simple cost and usage tracking (preventive control).</li> 
 <li><a href="https://aws.amazon.com/aws-cost-management/aws-cost-anomaly-detection/">Anomaly Detection</a> is an AWS Cost Management feature that uses machine learning to continuously monitor your cost and usage to detect unusual spends; it’s a detective control, but if you integrate it with <a href="https://aws.amazon.com/sns/">Amazon Simple Notification Service</a> (SNS) and Lambda it becomes a responsive control.</li> 
</ul> 
<p>The real question here is: How we can speed up the process of budget allocation without slowing down the creation of a new account? There are, of course, many ways to do this. Usually, a company’s business units already have a budget allocated, so you need only to reallocate it on the accounts.</p> 
<p>For example, we can implement a budget allocation process between builders and product owners using <a href="https://aws.amazon.com/chatbot/">AWS Chatbot</a>. The builders ask for a new account on a Slack channel, and the product owner answers “yes” and sets the budget running <a href="https://aws.amazon.com/cli/">AWS Command Line Interface</a> (CLI) commands in the channel.</p> 
<h2>Summary</h2> 
<p>Governance in the cloud is a mix of process, people, and technologies that drive cloud adoption and improve an organization’s agility without compromising safety. Remember, I use the term “safety” because cloud governance is not only about (cyber) security.</p> 
<p>Creating a decentralized governance permits great control over standards and costs (safety) while allowing better responsiveness (agility). It’s important to develop a critical mass of people with AWS experience, establishing operational processes, and forming a <a href="https://aws.amazon.com/blogs/enterprise-strategy/using-a-cloud-center-of-excellence-ccoe-to-transform-the-entire-enterprise/">Cloud Center of Excellence</a> (CCoE) that’s dedicated to mobilizing the appropriate resources and defining best practices.</p> 
<p>Using <a href="https://aws.amazon.com/products/management-and-governance/">AWS Management and Governance services</a>, the CCoE can provide preconfigured services or resources to builders, and define preventive and detective controls that reduce vulnerabilities and maintain compliance across the organization.</p> 
<h6><em>The content and opinions in this blog are those of the third-party author and AWS is not responsible for the content or accuracy of this post.</em></h6> 
<p><span style="color: #ffffff;">.<br /> <a href="https://partnercentral.awspartner.com/PartnerConnect?id=001E000000ZLAC7IAP&amp;source=Blog&amp;campaign="><img alt="Claranet-APN-Blog-CTA-1" class="aligncenter size-full wp-image-23838" height="200" src="https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2021/03/22/Claranet-APN-Blog-CTA-1.png" width="800" /></a><br /> .</span></p> 
<hr /> 
<h2>Claranet – AWS Partner Spotlight</h2> 
<p><strong>Claranet</strong> <strong>is an AWS Premier Consulting Partner</strong> and a European leader in application management that specializes in providing managed AWS solutions to mid-size organizations.</p> 
<p><a href="https://partnercentral.awspartner.com/PartnerConnect?id=001E000000ZLAC7IAP&amp;source=Blog&amp;campaign=">Contact Claranet</a> | <a href="https://partners.amazonaws.com/partners/001E000000ZLAC7IAP/Claranet%20Group">Partner Overview</a></p> 
<p><strong>*Already worked with Claranet?</strong> <a href="https://partnercentral.awspartner.com/CreateReview?pid=001E000000ZLAC7IAP&amp;language=en">Rate the Partner</a></p> 
<p><em>*To review an AWS Partner, you must be a customer that has worked with them directly on a project.</em></p>
