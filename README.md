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




