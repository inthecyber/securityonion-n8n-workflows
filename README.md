# Automated Threat Intelligence Analysis with n8n and SecurityOnion

This project aims to enhance the efficiency of threat intelligence analysis through the implementation of automated workflows using [n8n](https://n8n.io/), integrated within [Security Onion](https://securityonionsolutions.com/). The primary goal is to streamline the initial alert triage process, enabling SOC analysts to conduct their analyses with greater simplicity and speed.  

The workflows are designed to support the analytical skills of SOC analysts, ensuring that they can focus on critical decision-making rather than getting bogged down in repetitive tasks. While the current workflows may lack strict input validation, the emphasis has been on functionality and rapid deployment for internal use.  

Recognizing the value and impact of automation in the SOC environment, this project is committed to exploring additional automation opportunities to further improve operational capabilities. 

Any contribution, feedback or idea is welcome.

### Technical Details

* `workflows/IP_Reputation.json` is the **IP workflow** described in the blog post.
* `workflows/Hash_Reputation.json` is the **Hash workflow** described in the blog post.
* `workflows/Domain_Reputation.json` is the **Domain workflow** described in the blog post.
* `workflows/CVE_Info.json` is the **CVE Info workflow** described in the blog post.
* `workflows/Dispatcher.json` is the **Dispatcher workflow** described in the blog post.

We used a self-hosted instance of n8n 1.50.0 and Security Onion 2.4.90 for this project. In order to integrate the workflows in Security Onion, we customized the Action menu by adding the following code under `Administration –> Configuration –> soc –> actions`. Change `<your-n8n-instance-name>` accordingly to your deployment.

```json
{"description":"IP Reputation","icon":"fa-external-link-alt","links":["https://<your-n8n-instance-name>/webhook/reputation?ip={value}"],"name":"IP Reputation","target":"_blank"}
{"description":"Domain Reputation","icon":"fa-external-link-alt","links":["https://<your-n8n-instance-name>/webhook/reputation?domain={value}"],"name":"Domain Reputation","target":"_blank"}
{"description":"Hash Reputation","icon":"fa-external-link-alt","links":["https://<your-n8n-instance-name>/webhook/reputation?hash={value}"],"name":"Hash Reputation","target":"_blank"}
{"description":"CVE Info","icon":"fa-external-link-alt","links":["https://<your-n8n-instance-name>/webhook/reputation?cve={value}"],"name":"CVE Info","target":"_blank"}
```

We put `<your-api-value>` inside every field and account in the workflows that required the use of API. Please change them accordingly.

### Contributors

Marco Pedrinazzi, Tommaso Tosi.

This project is licensed under the GNU General Public License v3.0.
