# Joomla Engineered by OCTOPODAMI (JEBO) SSL

You can secure your Octopodami installation with an SSL certificate by following the instructions below.

+ Log in to your domain registrar.
+ Update your domain `A` or `CNAME` record to point to the EC2 Instance IP Address.
+ Wait for 15-20 minutes so DNS can propagate.
+ Log in to the EC2 instance via the terminal.
+ Set your domain name in the Nginx configuration and reload the service:

```sh
sudo sed -i 's/server_name _;/server_name mydomainname.com;/' /etc/nginx/conf.d/joomla.conf
sudo nginx -t && sudo systemctl reload nginx
```

+ Install Certbot and request the certificate:

```sh
sudo dnf install -y certbot python3-certbot-nginx
sudo certbot --nginx -d mydomainname.com
## Answer all the questions (this is a comment)
## Then, specify your domain name (this is a comment)
```

+ Test the renewal:

```sh
sudo certbot renew --dry-run
```

+ Access your domain name (`https://mydomainname.com`) and unlock the site with the instance ID as usual.

Joomla builds its links from the incoming request, so you do not need to change a site URL setting after you add the domain. The unlock page still applies over HTTPS.

## Links

1. [Marketplace Listing](https://aws.amazon.com/marketplace/pp/prodview-i3dd22kr2q7ti)
2. [EULA](./octopodamiEULA.txt)
3. [Knowledgebase](https://github.com/cloudeyalimited/joomla-engineered-by-octopodami/-/wikis/home)
4. [Issue Tracking](https://github.com/cloudeyalimited/joomla-engineered-by-octopodami/-/issues)
5. [Changelog](./changelog.md)

## Support

[Email](mailto:tech@cloudeya.org) support is available to Amazon Web Services Marketplace Customers. We do not offer refunds, but you may terminate your Joomla Engineered by OCTOPODAMI (JEBO) Stack at any time.

## License

The documentation is published under [BSD 3-Clause License](license.txt).

## Copyright

(c) 2020 - 2026 [Cloudeya Limited](https://cloudeya.org).
