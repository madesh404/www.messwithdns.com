# 🌐 Mess With DNS Experiment: Website + Email Routing

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
