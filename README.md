**Basic DNS Setup for GitHub Pages and DigitalOcean Droplet**
[roadmap.sh](https://roadmap.sh/projects/basic-dns)

This guide will help you set up DNS records for GitHub Pages and a DigitalOcean Droplet. Assuming you already have a domain and a server, let's get started.

### Task #1 - Setting Up a Custom Domain for GitHub Pages

1. **Go to Your DNS Management Page**
   - Log in to your domain registrar account (e.g., Cloudflare, Namecheap, GoDaddy).
   - Find your domain, then go to the DNS management or settings section.

2. **Create a CNAME Record**
   - **Record Type**: Select **CNAME**.
   - **Name**: Enter `www` (so `www.yourdomain.com` points to GitHub Pages).
   - **Value/Target**: Enter `yourusername.github.io` (replace `yourusername` with your GitHub username).
   - **TTL**: Leave it as the default or set it to **Automatic**.

3. **Create an A Record (Optional)**
   - If you want your domain (`yourdomain.com` without `www`) to also point to GitHub Pages, create an **A record**:
     - **Record Type**: Select **A**.
     - **Name**: Leave it empty or use `@` (to represent the root domain).
     - **Value/Target**: Enter GitHub's IP addresses. Use the following IP addresses:
       - `185.199.108.153`
       - `185.199.109.153`
       - `185.199.110.153`
       - `185.199.111.153`
   - You need to create four separate A records, one for each IP address.

4. **Configure GitHub Pages**
   - Go to your repository settings on GitHub.
   - Scroll down to the **GitHub Pages** section.
   - Under **Custom Domain**, enter your domain (e.g., `yourdomain.com`).
   - GitHub will automatically verify and link your domain.

5. **Wait for Propagation**
   - DNS changes may take a few minutes to a few hours to propagate worldwide. You can use tools like [DNS Checker](https://dnschecker.org/) to verify the changes.

### Task #2 - Setting Up a Custom Domain for DigitalOcean Droplet

1. **Get Your Droplet's IP Address**
   - Log in to DigitalOcean and go to your Droplets.
   - Copy the public **IPv4** address of your Droplet.

2. **Go to Your DNS Management Page**
   - Log in to your domain registrar account again and navigate to the DNS management page for your domain.

3. **Create an A Record**
   - **Record Type**: Select **A**.
   - **Name**: Leave it empty or use `@` (to represent the root domain).
   - **Value/Target**: Enter the IP address of your DigitalOcean Droplet.
   - **TTL**: Leave it as the default or set it to **Automatic**.

4. **Create a Second A Record for WWW**
   - **Record Type**: Select **A**.
   - **Name**: Enter `www` (so `www.yourdomain.com` also points to the Droplet).
   - **Value/Target**: Use the same IP address as your Droplet.

5. **Verify the Setup**
   - Open your browser and enter your domain (e.g., `yourdomain.com`).
   - You should see your static site hosted on your DigitalOcean Droplet.

### Final Notes
- **Propagation Time**: Like with GitHub Pages, DNS changes for the Droplet may take some time to propagate.
- **SSL Setup**: To secure your domain with HTTPS, you can use **Let's Encrypt**. This is optional but highly recommended for both GitHub Pages and your Droplet.

Feel free to add screenshots as you go through the steps. This will make it easier for you to remember the setup process in the future.

