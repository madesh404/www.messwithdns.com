# 🌐 Mess With DNS Experiment: Website + Email Routing & Authentication

## 📌 Overview

This project demonstrates how the Domain Name System (DNS) is used to route both:

- 🌐 Web traffic (using CNAME records)
- 📧 Email traffic (using MX records)

The experiment was completed using [Mess With DNS](https://messwithdns.com), Netlify, and Fastmail.

---

## 🧪 Experiment Goals

The purpose of this lab was to understand:

- How DNS maps domain names to services
- How websites are connected to hosting providers
- How email is routed using MX records
- How different DNS record types control different internet services

---

# 🌐 Part 1: Website Setup (Netlify + CNAME)

## 🔧 Setup Steps

1. Created a simple static website using HTML
2. Deployed the site using Netlify
3. Received a Netlify-generated domain (e.g. `random-site.netlify.app`)
4. Configured a custom domain on Netlify:

www.squid366.messwithdns.com

5. Added a CNAME record in Mess With DNS:

www → random-site.netlify.app


## 📡 Result

Visiting:


http://www.squid366.messwithdns.com


successfully loads the Netlify-hosted website.

---

## 🧠 Key Concept Learned

- A **CNAME record** maps a domain to another domain.
- DNS resolves the alias to the actual hosting provider.
- Web hosting services like Netlify rely on DNS for routing traffic.

---

# 📧 Part 2: Email Setup (Fastmail + MX Records)

## 🔧 Setup Steps

1. Signed up for Fastmail
2. Configured a custom email domain:

you@mail.squid366.messwithdns.com

3. Added two MX records in Mess With DNS:

mail → in1-smtp.messagingengine.com (priority 10)
mail → in2-smtp.messagingengine.com (priority 20)

4. Sent a test email from Gmail to:

you@mail.squid366.messwithdns.com

5. Email successfully arrived in Fastmail inbox

---

## 📡 Result

Email routing worked successfully using DNS MX records.

---

## 🧠 Key Concept Learned

- **MX records** define mail servers responsible for receiving email.
- DNS is used to route email traffic before SMTP delivery begins.
- Email delivery relies on multiple systems working together:
- DNS (routing)
- SMTP (sending)
- Mail server (storage)

---

# 🔐 Part 3: Email Authentication (SPF + DKIM)

## 🎯 Objective

The goal of this experiment was to configure SPF and DKIM DNS records so that outgoing email from the custom domain could be authenticated by receiving mail servers.

This helps prevent email spoofing and improves email deliverability by proving that messages are authorized by the domain owner.

---

## 🔧 Setup Steps

1. Completed the custom email setup from Part 2 using Fastmail.
2. Followed Fastmail's domain authentication instructions.
3. Added the required SPF TXT record to DNS.
4. Added the required DKIM CNAME records to DNS.
5. Waited for DNS propagation.
6. Verified that Fastmail detected the records successfully.
7. Sent a test email from the custom domain to a Gmail account.
8. Examined the email headers using Gmail's **Show Original** feature.

---

## 📡 DNS Records Configured

### SPF Record

SPF (Sender Policy Framework) specifies which mail servers are authorized to send email on behalf of the domain.

```text
Type: TXT
Value: v=spf1 include:spf.messagingengine.com ?all
```

### DKIM Records

DKIM (DomainKeys Identified Mail) uses cryptographic signatures to verify that outgoing messages are authentic and have not been modified.

Three DKIM CNAME records were configured:

```text
fm1._domainkey.mail.squid366.messwithdns.com
fm2._domainkey.mail.squid366.messwithdns.com
fm3._domainkey.mail.squid366.messwithdns.com
```

---

## ✅ Verification

The SPF and DKIM records were verified using multiple methods:

### DNS Verification

Confirmed that DNS records were publicly resolvable using:

```bash
nslookup -type=TXT mail.squid366.messwithdns.com
nslookup fm1._domainkey.mail.squid366.messwithdns.com
```

### Gmail Verification

A test message was sent from the Fastmail account to Gmail.

Using Gmail's **Show Original** feature, the email headers reported:

```text
SPF=PASS
DKIM=PASS
```

Additionally, Gmail displayed:

```text
mailed-by: mail.squid366.messwithdns.com
```

confirming successful SPF validation.

---

## 🧠 Key Concepts Learned

### SPF (Sender Policy Framework)

SPF allows domain owners to specify which mail servers are permitted to send email on behalf of their domain.

Receiving mail servers check the SPF record during delivery and determine whether the sending server is authorized.

### DKIM (DomainKeys Identified Mail)

DKIM uses public-key cryptography to digitally sign outgoing messages.

The receiving mail server retrieves the public key from DNS and verifies the signature to ensure the message is authentic and has not been altered in transit.

---

# 🔍 What This Project Demonstrated

This project explored three major uses of DNS:

| Service              | DNS Record Type | Purpose                                  |
| -------------------- | --------------- | ---------------------------------------- |
| Website Hosting      | CNAME           | Route web traffic to Netlify             |
| Email Delivery       | MX              | Route incoming email to Fastmail         |
| Email Authentication | TXT / CNAME     | Verify outgoing email using SPF and DKIM |

The experiments demonstrated that DNS serves as a foundational internet service that directs traffic to the correct systems and enables secure communication between services.

---

## 🧠 Final Understanding

DNS acts as the **address book of the internet**, mapping human-readable domain names to different services:

- Websites → hosting providers
- Emails → mail servers
- Other services → specialized DNS records

---

## 🚀 Tools Used

- Mess With DNS: https://messwithdns.com
- Netlify: https://www.netlify.com
- Fastmail: https://www.fastmail.com

---

## 📌 Notes

- DNS records in this experiment are temporary and expire after ~1 week
- This setup is for educational purposes only
- Not intended for production use

---

## 🎯 Summary

This lab demonstrated a full end-to-end understanding of DNS by configuring both:

- A working website via CNAME records
- A working email system via MX records

Together, they show how DNS underpins nearly all internet communication.
