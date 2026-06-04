## 🌐 Mess With DNS Experiment: Website + Email Routing & Authentication

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

# 🔍 What This Experiment Proved

This project demonstrates that DNS is not just for websites.

It routes multiple types of internet services:

| Service | DNS Record Type | Example |
|--------|----------------|--------|
| Website | CNAME / A record | Netlify hosting |
| Email | MX record | Fastmail inbox |

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
