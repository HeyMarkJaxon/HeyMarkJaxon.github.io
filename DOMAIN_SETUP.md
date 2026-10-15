# Custom Domain Setup for GitHub Pages

This project intentionally includes `CNAME.example` rather than an active `CNAME` file until the exact domain is known.

## 1. Decide which address will be primary

Examples:

- Apex domain: `example.com`
- Subdomain: `www.example.com`

GitHub Pages supports both. Pick one primary address and configure your DNS provider so the other redirects or resolves appropriately.

## 2. Add the domain in GitHub first

In the portfolio repository:

**Settings → Pages → Custom domain**

Enter the exact domain and save it.

If you publish from a branch, GitHub can create the root `CNAME` file for you.

## 3. DNS for an apex domain

For `example.com`, GitHub currently documents these IPv4 A records:

- `185.199.108.153`
- `185.199.109.153`
- `185.199.110.153`
- `185.199.111.153`

Use record name `@` at most DNS providers.

GitHub also supports ALIAS/ANAME records if your provider offers them; those can point the apex to `YOUR_GITHUB.github.io`.

## 4. DNS for www

Create a CNAME record:

- Name/host: `www`
- Target/value: `YOUR_GITHUB.github.io`

Do not include the repository name in that target.

## 5. Verify and secure it

GitHub recommends verifying your domain to reduce domain-takeover risk. Avoid wildcard DNS records for GitHub Pages.

Once DNS is working, enable **Enforce HTTPS** under **Settings → Pages**. DNS/HTTPS changes can take time to propagate.

## 6. Optional manual CNAME file

If needed, copy `CNAME.example` to a file named exactly `CNAME` and replace its contents with one domain only, for example:

`example.com`

The file must contain only the domain name—not `https://` and not a path.
