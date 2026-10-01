Here are the step-by-step instructions to connect your **Namecheap** domain to your deployed **Vercel** project:

---

### Step 1: Add your domain in Vercel

1. Open your [Vercel Dashboard](https://vercel.com/dashboard) and click on your deployed project.
2. Click **Settings** in the top navigation bar, then select **Domains** from the left sidebar.
3. In the input box under "Add Domain", type your full domain name (e.g., `yourdomain.com`).
4. Click **Add**.
5. Select the **Recommended** option (this handles both `yourdomain.com` and `[www.yourdomain.com](https://www.yourdomain.com)`).
6. Leave this tab open. Vercel will temporarily show an **Invalid Configuration** status—this is expected until you update Namecheap.

---

### Step 2: Configure DNS Records in Namecheap

1. Open a new tab and log into your [Namecheap Account](https://www.namecheap.com/).
2. Click **Domain List** on the left menu.
3. Find your domain and click the **Manage** button next to it.
4. Under the **Domain** tab, scroll down to **Nameservers**:
* Make sure it is set to **Namecheap BasicDNS** (or **Namecheap WebDNS**).
* *If it's set to Custom DNS, switch it back to Namecheap BasicDNS and click the green checkmark.*


5. Click the **Advanced DNS** tab near the top of the page.
6. Under the **Host Records** section, delete any existing default records (like default `A Record` pointing to Namecheap IP or `URL Redirect Record`) by clicking the **trash can** icon next to them.
7. Click **Add New Record** and create the following two records:

#### Record 1: Apex / Root Domain

* **Type:** `A Record`
* **Host:** `@`
* **Value:** `76.76.21.21`
* **TTL:** `Automatic` (or `1 min`)
* Click the **green checkmark** icon to save.

#### Record 2: WWW Subdomain

* **Type:** `CNAME Record`
* **Host:** `www`
* **Value:** `cname.vercel-dns.com.` *(include the trailing period if Namecheap accepts it, otherwise just `cname.vercel-dns.com`)*
* **TTL:** `Automatic` (or `1 min`)
* Click the **green checkmark** icon to save.

---

### Step 3: Verify & Complete Setup in Vercel

1. Switch back to your **Vercel Dashboard** > **Settings** > **Domains**.
2. Click the **Refresh** button next to your domain entries.
3. Wait a few minutes for DNS changes to propagate.
4. Once verified, the status will turn into a green checkmark indicating **Valid Configuration**.
5. Vercel will automatically issue a free SSL certificate for `[https://yourdomain.com](https://yourdomain.com)`.











Since you already purchased a **Namecheap Private Email** mailbox, you need to add Namecheap's MX and TXT records to your domain's **Advanced DNS** settings.

Follow these steps to connect your Namecheap Private Email:

---

### Step 1: Open Mail Settings in Namecheap

1. Log in to your [Namecheap Account](https://www.namecheap.com/).
2. Click **Domain List** on the left menu and click **Manage** next to your domain.
3. Select the **Advanced DNS** tab at the top.
4. Scroll down to the **Mail Settings** section.
5. In the dropdown menu, change the selection from *No Email / Email Forwarding* to **Custom MX**.

---

### Step 2: Add MX Records

In the **Mail Settings** section, add these two MX records:

| Record Type | Host | Priority | Value / Target |
| --- | --- | --- | --- |
| **MX Record** | `@` | `10` | `mx1.privateemail.com` |
| **MX Record** | `@` | `21` | `mx2.privateemail.com` |

*(Note: If Namecheap only asks for Priority and Value, set Priority to `10` for `mx1` and `21` or `10` for `mx2`)*.

---

### Step 3: Add TXT Records for Email Security (SPF & DKIM)

Scroll back up to the **Host Records** section on the same **Advanced DNS** page. Adding an SPF and DKIM record ensures your outgoing emails don't end up in spam folders.

Click **Add New Record** for each of the following:

#### 1. SPF Record (Prevents Email Spoofing)

* **Type:** `TXT Record`
* **Host:** `@`
* **Value:** `v=spf1 include:spf.privateemail.com ~all`
* **TTL:** `Automatic`

#### 2. Autoconfig CNAME (Optional, for easy setup in mail apps like Outlook / Apple Mail)

* **Type:** `CNAME Record`
* **Host:** `mail`
* **Value:** `privateemail.com.`
* **TTL:** `Automatic`

Click the **green checkmark** to save all new records.

---

### Step 4: Access Your Email

1. Wait around **5 to 30 minutes** for the DNS changes to propagate.
2. Go to **[privateemail.com](https://privateemail.com)**.
3. Log in using your full business email address (e.g., `info@yourdomain.com`) and the password you set up when purchasing the email plan in Namecheap.
