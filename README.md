# Quick Docker VPN

This project was made for a personal need for a VPN service with the ability to block ads, trackes and other malicious network activity. It uses WireGuard as the VPN protocol and AdGuard Home as the DNS server.

## Requirements

To ease and speed up the installation process, the project uses Docker and Docker Compose. So, you need to have both installed on your server.

-   Docker
-   Docker Compose

## How to use

1. Clone the repository and make sure docker server is running.
2. Start the services using the following command:

```bash
docker-compose up -d
```

3. Connect to the VPN server using the WireGuard client. You can find the configuration file in the `adguard/config/peer{n}` directory.

4. Before you can access the internet, you need to set up Adguard. To do this, open your browser and go to [http://10.10.0.10:3000](http://10.10.0.10:3000). Leave the default settings and create a new login with username and password. Once the setup is complete, you can start browsing the internet. The AdGuard Home dashboard is available at [http://10.10.0.10](http://10.10.0.10)`.

## How to add a new peer

1. Stop the services using the following command:

```bash
docker-compose down
```

2. Open the `docker-compose.yml` file and increment the `PEERS` environment variable by one.

3. Start the services again and find the new peer configuration file in the `adguard/config/peer{n}` directory.

## Configuration

The default DNS upstream servers are Quad9. Personally i prefer Cloudflares servers. To change the upstream servers, open the [http://10.10.0.10/#dns](http://10.10.0.10/#dns) page and change the upstream servers. Remember to save and test the connection.

Cloudflare DNS Servers:

-   1.1.1.1 (Standard)

Cloudflares blocking DNS Servers ([Cloudflare for families](https://blog.cloudflare.com/introducing-1-1-1-1-for-families/))

-   1.1.1.2 (Block Malware)
-   1.1.1.3 (Block Malware and Adult Content)
