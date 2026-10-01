Step 1: Add your domain in Vercel
Open your Vercel Dashboard and click on your deployed project.

Click Settings in the top navigation bar, then select Domains from the left sidebar.

In the input box under "Add Domain", type your full domain name (e.g., yourdomain.com).

Click Add.

Select the Recommended option (this handles both yourdomain.com and [www.yourdomain.com](https://www.yourdomain.com)).

Leave this tab open. Vercel will temporarily show an Invalid Configuration status—this is expected until you update Namecheap.

Step 2: Configure DNS Records in Namecheap
Open a new tab and log into your Namecheap Account.

Click Domain List on the left menu.

Find your domain and click the Manage button next to it.

Under the Domain tab, scroll down to Nameservers:

Make sure it is set to Namecheap BasicDNS (or Namecheap WebDNS).

If it's set to Custom DNS, switch it back to Namecheap BasicDNS and click the green checkmark.

Click the Advanced DNS tab near the top of the page.

Under the Host Records section, delete any existing default records (like default A Record pointing to Namecheap IP or URL Redirect Record) by clicking the trash can icon next to them.

Click Add New Record and create the following two records:

Record 1: Apex / Root Domain
Type: A Record

Host: @

Value: ip from vercel dashboard

TTL: Automatic (or 1 min)

Click the green checkmark icon to save.

Record 2: WWW Subdomain
Type: CNAME Record

Host: www

Value: value provided from vercel dashboard

TTL: Automatic (or 1 min)

Click the green checkmark icon to save.

Step 3: Verify & Complete Setup in Vercel
Switch back to your Vercel Dashboard > Settings > Domains.

Click the Refresh button next to your domain entries.

Wait a few minutes for DNS changes to propagate.

Once verified, the status will turn into a green checkmark indicating Valid Configuration.

Vercel will automatically issue a free SSL certificate for [https://yourdomain.com](https://yourdomain.com).
