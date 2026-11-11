# postiz-deploy

Docker Compose setup for running Assign, a rebranded fork of [Postiz](https://github.com/gitroomhq/postiz-app), on a VPS with Dokploy.

It uses the `ghcr.io/abahvictor360-sketch/assign-app:latest` image, built from github.com/abahvictor360-sketch/assign-app (Postiz rebranded to Assign). Nothing is built here.

The ghcr package must be public, or add ghcr.io credentials under Dokploy > Registry.

## Dokploy setup

1. Create a Compose service. Provider: GitHub, this repo, branch `main`, compose path `./docker-compose.yaml`.
2. Environment tab: paste the variables from `.env.example` and fill in real values.
3. Domains tab: service `postiz`, container port `5000`, HTTPS on, Let's Encrypt.
4. Deploy. First run pulls about 3 GB of images.
5. Sign up (first account is admin), then set `DISABLE_REGISTRATION=true` and redeploy.

The VPS needs about 4 GB RAM for Postiz plus the Temporal stack.

Secrets live only in Dokploy. This repo is public, so never commit a real value.
