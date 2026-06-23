@lab.Title

**Please enter your own Microsoft alias (without the @microsoft.com) in the field below before starting the lab**. This information is required to correctly associate your activity with your learner record and ensure your completion is accurately captured and reported. For data integrity and compliance reasons, learners may only enter their own alias.   After completing the lab, please allow up to 5 business days for all reporting systems to fully reflect your completion.

@lab.ActivityGroup(aliascapture)

===


## Survey

@lab.ActivityGroup(initialsurvey)

===

## Objectives
In this lab, you'll learn how to enable Defender for CSPM and leverage Defender for CSPM Capabilities

### Scenario

Adatum Corporation had a robust cybersecurity infrastructure in place. However, one day, an attacker used a brute force or password spraying attack to gain access to an Internet-exposed server of the organization.

The attacker could quickly move laterally through the network, exploiting vulnerabilities on the Internet-exposed servers and gaining access to the organization's Storage Accounts, SQL servers, and Key Vaults. The SOC department was alerted by Defender for Cloud on the "Brute Force, Password Spray" IOC/IOA, and quickly realized something was wrong when they noticed unusual activity on the servers and Storage Accounts.

In response to the attack, the security engineers leveraged the attack path analysis to identify the entry point of the attack and the path the attackers used to move laterally through the network. Based on this analysis, they were able to close the entry point and cut off the attackers' access to the organization's data.

Additionally, they utilized **Sensitive Data Discovery** to identify and secure sensitive information that could be at risk of exposure. **Permission Management** tools were implemented to review and tighten access controls, ensuring that permissions were strictly granted based on the principle of least privilege. The discovery of plaintext secrets in the environment prompted the integration of **Secret Discovery** tools to encrypt sensitive data and manage secrets more securely.

The IT department didn't stop there. They also took a proactive approach by implementing security recommendations to fix the vulnerabilities on the Internet-exposed servers and prevent similar attacks in the future. Utilizing the Risk Prioritization feature of DCSPM, the security team gained full visibility into which recommendations should be prioritized, focusing their efforts on addressing the most critical vulnerabilities first. Additionally, they implemented a robust incident response plan and conducted regular security training for employees. 

Thanks to the combination of both reactive and proactive measures, Adatum Corporation was able to prevent a major data breach and keep their sensitive information safe. This hypothetical use case demonstrates the importance of having both a reactive and proactive approach when it comes to cybersecurity, including performing attack path and security risk analysis, implementing security recommendations, assigning/managing change actions to the proper owners, and educating employees to prevent future attacks.  

In this exercise, we will explore the Attack Path feature of Defender CSPM. Through a hands-on scenario, you will learn how to identify and mitigate potential security breaches that exploit critical vulnerabilities and inadequate permission settings in cloud environments.

---

⌛ Estimated time to complete this lab: **60 minutes**

===

## Using this Lab

>[!hint] **Copy Text Supported** 
>  
> The fill in fields of this simulation require the exact text be entered to progress. To make that easier, you can select ++Copy Text++ options in the instructions pane to copy directly into your simulation text entry fields.


---

###**Images and diagrams**   

All images and diagrams in the lab instructions are selectable. Selecting any image opens a zoomed view in a separate window for better clarity and analysis. 

---

###**Split Window feature**   

If you're equipped with multiple screens, you can use the **Split Window** feature to place the lab instructions on a separate screen, making better use of your screen real estate.  


To enable this feature:   

1. Go to the **gear** ![q1lci4ku.png](../../media/q1lci4ku.png)icon in the upper-right corner of the instructions pane.   

1. At the bottom of the **Settings** pane, select **Split Windows**.

![zqktfacn.png](../../media/zqktfacn.png)


===

## Task 01: Enable Defender CSPM

1. From the Azure dashboard, select `Microsoft Defender for Cloud`.



	![exnodcpd.png](../../media/exnodcpd.png)

1. On the left side pane, select **Management**, then **Environment settings**.


1. On the lower side of the page, select **Expand all**.



	![gerx605h.png](../../media/gerx605h.png)

1. Select the **TechMaster-lod52521856** subscription.


1. Turn on **Defender CSPM**.



	![bkq1swe8.png](../../media/bkq1swe8.png)

1. In the upper-left corner of the page, select **Save**.



	>[!alert] The agentless scanning engines will begin their assessments and are expected to generate insights **within 24 hours**. In a real environment you would need to allow this time for the initial data collection and analysis to complete, then return to review the results.

===

## Task 02: Build queries with Cloud Security Explorer

You'll utilize Cloud Security Explorer in Microsoft Defender for Cloud to perform an ad-hoc risk analysis by querying and identifying risky resources within your cloud environment. You'll learn how to use predefined query templates and the query builder to enhance your understanding of how to effectively search for vulnerabilities in your environment.

---

1. In the upper-left corner of the page, select the **Microsoft Defender for Cloud | Environment settings** breadcrumb link.



	![mquqb1q9.png](../../media/mquqb1q9.png)

1. On the left side pane, select **General**, then **Cloud Security Explorer**.


1. Choose the **Select resource types** dropdown menu.



	![a653q64r.png](../../media/a653q64r.png)

1. Select **Compute**, expand **Virtual machines**, select **Azure Virtual machines**, then select **Done**.



   ![p8egjqrb.png](../../media/p8egjqrb.png)

1. Add a condition by selecting the **+** button. 



	![02nv6vmn.png](../../media/02nv6vmn.png)

1. Chose the **Select condition** dropdown menu.


1. Select **Vulnerabilities**, then **By severity**.



	![260dsl4f.png](../../media/260dsl4f.png)

1. Select the dropdown menu after **Equals**, then select **High**.


	
    ![1sve0st0.png](../../media/1sve0st0.png)

1. Below the query, select **Search**.


1. In the upper-right corner of the query, select **Clear all**.



	![shj7yd11.png](../../media/shj7yd11.png)

1. Move through the page and observe the prebuilt **Query templates** Azure provides for speeding your searches for common scenarios. Under the **Query templates** section, select the following prebuilt template: **User accounts with permission to vulnerable VMs**



    ![ihuv6b74.png](../../media/ihuv6b74.png)

	>[!note] This fills in the details for the query, which you can also adjust as needed.

1. Below the query, select **Search**.



	![o5tx5jxx.png](../../media/o5tx5jxx.png)

===

## Task 03: Assign a governance rule

You'll learn to establish and manage automated recommendation remediation assignment and configuration through MDC Governance rules within Microsoft Defender for Cloud. 

Assume the role of a security administrator at a large organization managing multiple Azure subscriptions. Your challenge is to automate the remediation process for high-severity vulnerabilities, ensuring they are addressed promptly to maintain a robust security posture.

You'll configure a governance rule that ensures all high-severity vulnerabilities are remediated within 90 days, enhancing the security and compliance of your cloud environment. This process not only helps maintain your organization's security posture but also introduces a structured approach to managing cloud resources responsibly.

---

1. On the left side pane, under **Management**, select **Environment settings**.


1. Select the **Governance rules** tile.



	![kifzu67y.png](../../media/kifzu67y.png)

1. On the top bar, select **+ Create governance rule**.


1. In the flyout pane:


1. Enter the following details:


    
        | Item | Value |
        |:---------|:---------|
        | Rule name | ++High Severity Remediation Standard - 90 Day SLA++ |
        | Scope | **TechMaster-lod52521856** |
        | Priority | ++100++ |

        ![25k5v47i.png](../../media/25k5v47i.png)

1. On the lower side of the pane, select **Next**.


1. Under the **Impacted recommendations** section, select **By severity**, then set to **High**.



		![bblcqg5y.png](../../media/bblcqg5y.png)

1. Under the **Set owner** section, enter the following details:


    
        | Item | Value |
        |:---------|:---------|
        | Owner | **By email address** |
        | Add user manually | ++User1-61416947@LODSPRODMCA.onmicrosoft.com++ |
        | Remediation timeframe | **90 days** |

        ![f5rr2un6.png](../../media/f5rr2un6.png)

1. On the lower side of the pane, select **Create**.


1. In the dialog, select the **Apply rule...** checkbox, then select **OK**.



    	![6ggfnx30.png](../../media/6ggfnx30.png)

1. On the top bar, select **Governance report**.



	![mxow4pt7.png](../../media/mxow4pt7.png)

1. You can view the status of tasks, categorized by **Complete**, **Overdue**, **On-time**, **Unassigned**.



	![dd9umv9a.png](../../media/dd9umv9a.png)

===

## Task 04: Analyze Security Recommendations by Risk Level - Risk Prioritization

You'll learn to use the risk prioritization feature in Microsoft Defender for Cloud to analyze and prioritize security recommendations based on their risk levels. This allows security teams to focus on the most critical issues that could impact the security posture of their cloud environments.

You're part of a security team managing cloud assets for a multinational corporation. Due to the vast number of assets and continuous deployment cycles, it's crucial to prioritize security tasks effectively. By focusing on high-risk recommendations, you can optimize your remediation efforts and allocate resources more efficiently.

---

1. In the upper-left corner of the page, select the **Microsoft Defender for Cloud | Environment settings** breadcrumb link.


1. On the left side pane, under **General**, select **Recommendations**.



	>[!knowledge] You can view multiple valuable insights as they are exposed through each column of the records. You can see the risk factors that have contributed to the risk level evaluation, the number of attack paths found for the resource, whether an owner has been assigned to its remediation, and the status of the change.

1. Go through the recommendations and select the risk recommendation: **Update wget**.



	![sfpbu3tk.png](../../media/sfpbu3tk.png)
	
	>[!knowledge] You can view detailed information about the risk factors, affected resources, and suggested remediation steps.

1. Observe the recommendation's details to understand the potential business impact and the exploitability of the vulnerability.


1. At the top of the rightmost pane, select the **Associated CVEs** tab.


1. Select the only item **CVE-2024-38428**.



	![c04qv216.png](../../media/c04qv216.png)

	>[!note] Observe all the details it provides in the flyout pane.

---

With this information, you could plan and assign remediation tasks based on the priority of the risks. Use the integrated task management tools within Defender for Cloud to assign tasks to appropriate team members.

Monitor the progress of remediation efforts through the **Governance report** to ensure high-risk vulnerabilities are addressed in a timely manner.

===

## Task 05: Leverage cloud infrastructure entitlement management (CIEM)

You'll learn the process of enabling and using cloud infrastructure entitlement management (CIEM) in Microsoft Defender for Cloud. This feature helps manage and secure identity and access configurations across your cloud environments, ensuring that permissions adhere to the principle of least privilege.

As a security administrator, you're tasked with reducing the risk of excessive permissions in your organization's cloud environments. CIEM allows you to track and manage entitlements efficiently, enhancing security and compliance.

---

1. In the upper-left corner of the page, select the **Microsoft Defender for Cloud | Recommendations** breadcrumb link.


1. On the left side pane, under **Management**, select **Environment settings**.


1. On the lower side of the page, select **Expand all**.



	![94xoo3x0.png](../../media/94xoo3x0.png)

1. Select the **TechMaster-lod52521856** subscription.



	![fjalw4f1.png](../../media/fjalw4f1.png)

1. On the line for **Defender CSPM**, under the **Monitoring coverage** column, select **Settings**.



	![xtaxc81o.png](../../media/xtaxc81o.png)

1. Observe the line for **Cloud Infrastructure and Entitlements Management (CIEM)**, which was automatically enabled with **Defender CSPM**.



	>[!knowledge] Cloud Infrastructure Entitlement Management (CIEM) in Microsoft Defender for Cloud provides native visibility into who has access to what across cloud environments. CIEM discovers and analyzes effective permissions for human and non-human identities analyzing inactive, excessive, and risky access to multi-cloud resources, enabling enforce least-privilege access and reduce privilege escalation risk.

1. In the upper-left corner of the page, select the **Settings | Defender** breadcrumb link.



	![ctn67dgu.png](../../media/ctn67dgu.png)

1. On the left side pane, select **Security policies**.


1. Search for ++Azure CSPM++ and press **Enter**. Verify the policy is enabled.



	![pimrlcma.png](../../media/pimrlcma.png)

	>[!knowledge] This will grant you access to the permissions management features through the Defender for Cloud portal.

1. In the upper-left corner of the page, select the **Microsoft Defender for Cloud | Environment settings** breadcrumb link.


1. On the left side pane, under **General**, select **Recommendations**.


1. In the search box, type ++permissions++ and press **Enter**, to view the related recommendations.



	![e67wfdeb.png](../../media/e67wfdeb.png)

---

>[!knowledge] Use CIEM's capabilities to analyze and adjust permissions across your Azure, AWS, or GCP resources.
>
>For further details on using CIEM, refer to the official [Microsoft documentation](https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-permissions-management).

===

## Task 06: Analyzing and mitigating attack paths

### Scenario Overview

An Internet-exposed VM has been identified with High severity vulnerabilities, which includes read permissions to a key vault. This setup poses a significant risk as it may allow attackers to exploit Remote Code Execution (RCE) vulnerabilities on the server. The lack of "least privileged" permission configurations could enable intruders to access sensitive secrets stored in the Key Vault once the server is breached.

### Objective

Utilize the Attack Path feature to trace and understand how an attacker could navigate through your cloud environment and identify critical steps to mitigate this risk.

The next exercise will demonstrate how to leverage the Attack Path feature of Defender for CSPM, highlighting a critical use case where an Internet-exposed VM with High severity vulnerabilities and read permissions to a key vault presents a potential attack vector.

---

1. On the left side pane, under **General**, select **Attack path analysis**.


1. Select **Internet exposed Azure VM with high severity vulnerabilities allows lateral movement to Azure Key Vault**.



	![r6drjqlb.png](../../media/r6drjqlb.png)

1. Observe the page.



	![3ajfwazw.png](../../media/3ajfwazw.png)

    >[!knowledge] You can observe the attack path and the resources involved in the attack vector. By select each node/element of the attack path, you can review detailed information. The rightmost pane provides related insights and valuable information, helping you understand how the attack can occur and what factors contribute to the lateral movements through the resources involved.

1. In the rightmost pane, select the **dcspmlab-winsrv** node.



	![keqt9pus.png](../../media/keqt9pus.png)

1. In the flyout pane, select the **Recommendations** tab.



	![blfbu1kz.png](../../media/blfbu1kz.png)

1. At the top of the attack path view, select the **Remediation** tab.



	![evb94bzv.png](../../media/evb94bzv.png)

    ![qtl3nckx.png](../../media/qtl3nckx.png)

	>[!note] This displays the specific security recommendations needed to mitigate attack vectors.

1. Try selecting **Update windows_server_2019**.


1. Observe the page, and note the remediation steps it provides in the rightmost pane.



	![tj50tb10.png](../../media/tj50tb10.png)

=== 
>[!Alert] **IMPORTANT:** These labs are hosted on the Skillable platform. Completion data is collected and then exported to Success Factors every Monday. SF require another 1-3 days to process that data. The status for this lab will be visible in Viva and Learning Path next week. 
>
Be sure to select "**Submit**" in the bottom right corner to get credit for completing this lab. 

@lab.ActivityGroup(completionsurvey)

>[!Alert] After answering the survey questions, select **submit** to complete and end the lab. **This is required in order to receive credit for lab completion**.

