# Hosts

[![Run](https://github.com/Ryanjiena/Hosts/actions/workflows/run.yml/badge.svg)](https://github.com/Ryanjiena/Hosts/actions/workflows/run.yml)

<!-- hosts start -->

```
# Hosts From: [https://github.com/Ryanjiena/Hosts]
# Generated: 2022-11-13 21:01:06

140.82.112.26		alive.github.com
140.82.113.25		live.github.com
185.199.108.154		github.githubassets.com
185.199.109.154		github.githubassets.com
140.82.112.22		central.github.com
185.199.108.133		desktop.githubusercontent.com
185.199.108.153		assets-cdn.github.com
185.199.109.153		assets-cdn.github.com
185.199.108.133		camo.githubusercontent.com
185.199.108.133		github.map.fastly.net
151.101.1.194		github.global.ssl.fastly.net
140.82.114.3		gist.github.com
185.199.108.153		github.io
185.199.109.153		github.io
140.82.112.4		github.com
140.82.112.6		api.github.com
185.199.108.133		raw.githubusercontent.com
185.199.108.133		user-images.githubusercontent.com
185.199.108.133		favicons.githubusercontent.com
185.199.108.133		avatars5.githubusercontent.com
185.199.108.133		avatars4.githubusercontent.com
185.199.108.133		avatars3.githubusercontent.com
185.199.108.133		avatars2.githubusercontent.com
185.199.108.133		avatars1.githubusercontent.com
185.199.108.133		avatars0.githubusercontent.com
185.199.108.133		avatars.githubusercontent.com
140.82.113.10		codeload.github.com
52.217.196.17		github-cloud.s3.amazonaws.com
52.216.249.100		github-com.s3.amazonaws.com
52.217.104.180		github-production-release-asset-2e65be.s3.amazonaws.com
52.217.40.92		github-production-user-asset-6210df.s3.amazonaws.com
52.216.146.203		github-production-repository-file-5c1aeb.s3.amazonaws.com
185.199.108.153		githubstatus.com
185.199.109.153		githubstatus.com
140.82.112.17		github.community
52.224.38.193		github.dev
140.82.114.21		collector.github.com
13.107.43.16		pipelines.actions.githubusercontent.com
185.199.108.133		media.githubusercontent.com
185.199.108.133		cloud.githubusercontent.com
185.199.108.133		objects.githubusercontent.com
13.107.213.51		vscode.dev
13.32.151.9		plugins.jetbrains.com
172.253.112.95		translate.googleapis.com
172.253.63.94		update.googleapis.com
34.120.54.55		deno.dev
```

<!-- hosts end -->

## Usage

### Linux

```bash
mv /etc/hosts /etc/hosts.gc.bak

cp /etc/hosts.gc.bak /etc/hosts -f && curl -s https://hostsa.vercel.app/hosts | sudo tee -a /etc/hosts

# Clear or flush DNS cache
systemctl restart nscd.service
```

<details>
<summary>Run with systemd</summary>

```bash
#!/usr/bin/env bash
current_dir=$(cd -P -- "$(dirname -- "$0")" && pwd -P)
service="update_hosts"

mv /etc/hosts /etc/hosts.gc.bak

cat <<EOF > ${current_dir}/${service}.sh
#!/usr/bin/env bash
cp /etc/hosts.gc.bak /etc/hosts -f && curl -s https://hostsa.vercel.app/hosts | sudo tee -a /etc/hosts

EOF

chmod u+x ${current_dir}/${service}.sh

cat <<EOF > /etc/systemd/system/${service}.service
[Unit]
Description=Update hosts

[Service]
ExecStart=${current_dir}/${service}.sh

[Install]
WantedBy=default.target

EOF

systemctl start ${service}
systemctl enable ${service}
# systemctl stop ${service}
# systemctl disable ${service}
```

</details>

### Windows

1. Install [Chocolatey](https://chocolatey.org/install) / [Scoop](https://scoop.sh/)

2. Install [SwitchHosts](https://github.com/oldj/SwitchHosts)

   ```powershell
   choco install switchhosts
   scoop install switchhosts
   ```

3. Add new rules:

   - Title: `hostsa`
   - Type: `Remote`
   - URL: `https://hostsa.vercel.app/hosts`
   - Auto Refresh: `24 hours`

4. Clear or flush DNS cache: `ipconfig /flushdns`

## Thanks

- [521xueweihan/GitHub520](https://github.com/521xueweihan/GitHub520)

## License

Copyright (c) 2022 [Ryanjiena](https://github.com/Ryanjiena).

Licensed under the [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) license.
