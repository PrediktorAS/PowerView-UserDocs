# Cyber Security

PowerView™ solution with software and hardware/infrastructure is installed and maintained to secure data and to prevent system for unauthorized access and cyber-attacks.
Prediktor cooperate with customer IT personnel and supplier of other services to make sure best possible security. Network, routers, firewalls, etc. are in most cases delivered and configured by 3. Party IT suppliers. In these cases, Prediktor assist with requirements and recommendations to configure a secure system.
Information security is handles as a separate task within the company, and Prediktor is ISO 27001 certified. 
Below, certain subtopics within cyber security in PowerView™ is described in more details.

![CyberSecurity1](../images/CyberSecurity1.png)

## PowerView™ applications and data
To protect PowerView™ application from unauthorized access, some general rules are applied on the application level:
- Authentication with username and password
    - Possible to integrate with customer AD. 
    - Login and access are logged in database and available for audit
- Authorization with access control groups for different functions and features in PowerView™ web portal
- APIs protected with authentication 
- Sufficient password complexity level and password stored securely
- Password encrypted in user database and applications
- Web application with secure communication (SSL and certificates)
- Real time data communication from site to portfolio with OPC UA communication. This is secured using OpenSSL with message security
- Historian data replication services with message security

## PowerView™ Site Server (plant connector)
This is a server/PC running Windows OS operating system and hosting the PowerView™ software. 
The site server running the PowerView™ application on site for data acquisition and plant SCADA has connection to plant network to access local devices and to internet to provide data to the PowerView™ portfolio server. Since this server has access to production critical devices on network like inverters and substation control devices, it is important that this is protected from unauthorized access and that possible attacks are monitored and reported. 
Following is done to protect the site server and its application:
- Up to date OS versions
- Separate network connection to internet router and production network
- Windows firewall on and configured with only necessary port opened.
- Windows updated regularly with patches for optimal security
    - Automatic updates or controlled manual periodic updates.
- VPN network established for communication with portfolio server, one out of:
    - VPN router and point-to-point network established by customer IT supplier.
    - Point-to-Site Azure VPN connection to Azure VPN Gateway
- Site server not configured with public IP address.
- OPC UA data communication from site server to portfolio server with built in security and certificates.
- Historian data replication with message security
- Virus and malware software enabled and running on site server (Windows Defender). Mail reporting on incidents and attacks.

In addition, site network devices should be protected by firewall router maintained by IT personnel, protecting all devices on plant from unauthorized access. Same rules with minimal port opening should be maintained. 

## PowerView™ Portfolio Server
This is a server running Windows OS operating system and hosting the PowerView™ software. 
Server can be hosted on-premises at customer, in private cloud or in Azure cloud services by Prediktor.
For on-premises and private cloud, server is normally maintained by customer IT company, and Prediktor only provide recommendations and requirements.
Following is done to protect the server and its applications:
- Up to date Windows Server OS
- Windows firewall on and configured with only necessary port opened.
- Windows OS updated regularly with patches for optimal security.
- VPN network established for communication with site server, one out of
    - VPN router and point-to-point network established by IT supplier.
    - Azure VPN Gateway
- OPC UA data communication from site server to portfolio server with built in security and certificates.
- Site servers access using RDP access through secure VPN tunnel. 
- Access of databases and applications only to authorized personnel (username / password) and communication through ports allowed in firewall.
- Virus and malware software enabled and running on site server (Windows Defender). Mail reporting on incidents and attacks.

In addition, site network devices should be protected by firewall router maintained by IT personnel, protecting all devices on plant from unauthorized access. Same rules with minimal port opening should be maintained. 

## Information Security – ISO 27001
Prediktor is certified based on ISO 27001 standard for information security. Certification will be done on internal system, but procedures will also be applied for customer deliveries and solutions. Main tasks handled:
- Information Security Policy
- Information Classification Policy
- Acceptable Use of Assets Policy
- Access to Network and Network Services Policy
- Password Management Policy

## Security audits
Security audits on installed solution can be carried out on customer request. 
