# Steps to Set Up an NGINX Container and Configure Cloudflare

1. **Create an NGINX Container**

2. **Configure Cloudflare**

   - **CNAME Entry Configuration:**
     - **Type:** CNAME
     - **Name:** *
     - **Target:** bxtgeek.site
     - **Proxy Status:** None (DNS only)
     - **TTL:** Auto

   - **A Record Configuration:**
     - **Type:** A
     - **Name:** bxtgeek.site
     - **Target:** 192.168.1.95 (NGINX proxy IP)
     - **Proxy Status:** Reserved IP (DNS only)
     - **TTL:** Auto

3. **Add SSL Certificates**

   - Log in to the NGINX and select SSL certificates.
   - Click on "ADD SSL Certificate" and select Let's Encrypt.
   - In the domain name field, enter `bxtgeek.site` and `*.bxtgeek.site`.
   - Select "Use a DNS Challenge".
   - Choose Cloudflare as the provider.
   - Log in to Cloudflare and create an API token with "Edit zone DNS" permissions.
   - Once the API token is generated, log back into the NGINX Proxy Manager and complete the DNS challenge.

4. **Completion**

   - Once everything is set up, you will have your NGINX Proxy Manager configured with the wildcard certificate.
