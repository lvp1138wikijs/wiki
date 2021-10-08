---
title:  SSL Procedure of Shared / Web Hosting Plans 
description: 
published: true
date: 2021-10-08T12:46:52.084Z
tags: 
editor: markdown
dateCreated: 2021-10-08T12:46:52.084Z
---

This procedure is only for shared web hosting plan. For Dedicated/VPS plan please check the tutorial ([SSLCertificates](/TechnicalSupport/SSLCertificates))

Premaid replies (Need to add link)

SSL price has changed on our new web hosting plan.Now customers can purchase dedicated ips and ssl certificate from their client portal.

Price details:

Dedicated IP  : $4.95/mo

SSL:  

Quick SSL: $89.95/year
Quick SSL Premium: $149.95/year

Login to Client portal >> Menu >> SSL, certificates and IPs >> Setup SSL for a website.

> Note on Email Address
> Validation email can only be sent to an email attached to the domain. like admin@domain.com or administrator / hostmaster / webmaster / postmaster /or support@domain.com. Those are the options and is for security reasons to prove they own the domain. Inform customer create and configure an email account with any of it before we generating CSR
{.is-info}



## Step 1: Enable SSL

    Click on "Set up SSL for a website >> Enable SSL"
    Enabling SSL will assign a unique IP number to the selected website. Your website will continue responding on its existing IP number to allow for a smooth transition. Once enabled, you can browse your website using https:// as well as the standard http://.
    Select the website from " Website to enable SSL to " and then click on OK (Tick mark) button
    
    
    Once the SSL enabled on website then the system will assign a dedicated IP address on that website. 
    
    
## Step 2: Purchase SSL Certificate

After you enabled SSL feature on a website, then  click on the "SSL Certificates " option

    Step 1: Select the option " Purchase a secure certificate, through us, starting at $89.95 per year ". It will show an new option to select the SSL enabled websites.
    Step 2: Choose the SSL enabled website from the drop down list.
    Step 3: Choose the SSL type, Years and verify  the contact address in the new form and then click on OK (Tick) button.
    
    
    Once the order process complete then you will get the following message
    
    SSL

> Success...
> 
> An order for a certificate for polishpotterystore.com has been placed. Please check your email within the next ten minutes.
{.is-info}



## Step3: Install SSL Certificate

After you completed the above steps, then an approval email will send to your contact address. Go ahead and approve that email. 

After completing the verification process for your secure certificate, you will receive an email with the certificate itself.

Now go to Client portal >> Menu >> SSL, certificates and IPs again. Then you will see an option for install certificate on the website you purchased SSL.

Click on the Install button and  copy and paste the SSL certicate under " Paste Certificate ", including the BEGIN and END lines

Then click on OK (Tick) button.

That's all. You have now successfully installed SSL certificate on your website.



## **Renew SSL on Shared Hosting Account**


    Tell customer add payment to his account as credit
    Remove the payment using One Time
    Inform Minerva to renew the SSL cert on that specific domian. We can use the customer existing details to renew SSL cert
    Once the cert is reissued then an approval email will send to customer. Tell him to go ahead and approve it. After that he will receive a new email with the new cert and CA.

    If whois privacy is enabled for the domain.
    The contact email for the domain will be shown as "domain.com@contactprivacy.com".
    Please note that the validation email can only be sent to an email attached to the domain.
    Like admin@domain.com or administrator/hostmaster/webmaster/postmaster/or support@domain.com.
    Those are the options and is for security reasons to prove they own the domain.
    We  have to set the contact email first before purchasing the SSL certificate.
    Ask him for both and then forward it to James to install new cert.