# Zero to Deployed 🚀🌐

[![Sponsored by Stackaura](https://img.shields.io/badge/Sponsored_by-Stackaura_&_Ahmar_Hussain-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://www.stackaura.com/)
[![Deployment Guides](https://img.shields.io/badge/Guides-Deployment-007acc.svg?style=for-the-badge&logo=docker)](https://www.stackaura.com/)

A comprehensive collection of copy-paste deployment templates and guides to get your applications from `localhost` to production in minutes. No more fighting with obscure configurations.

---

<div align="center">
  <h3>Sponsored by <a href="https://www.stackaura.com/">Stackaura</a> & Ahmar Hussain</h3>
  <p>Helping modern engineering teams build and deploy faster.</p>
  <a href="https://www.stackaura.com/"><img src="https://img.shields.io/badge/Explore_Stackaura-Black?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Explore Stackaura" /></a>
</div>

---

## 🌟 What is this?

Have you ever finished a weekend project only to spend the next two weeks trying to deploy it? `zero-to-deployed` is an open-source repository containing ready-to-use configuration files for the most popular frameworks and infrastructure providers.

We cover everything from static sites on Vercel to containerized microservices on AWS EC2.

## 📂 Available Guides & Templates

### ☁️ Serverless & Edge (Vercel, Netlify, Cloudflare)
- Next.js on Vercel (Optimized for Edge caching)
- React/Vite to Cloudflare Pages
- Nuxt 3 to Netlify 

### 🐳 Containerized (Docker, AWS ECS, DigitalOcean)
- Node.js/Express Dockerfile + `docker-compose.yml`
- Python FastAPI to DigitalOcean App Platform
- Go API backend to AWS EC2 via GitHub Actions

### 🗄️ Databases (Postgres, Redis, MongoDB)
- Supabase integration templates
- PlanetScale automated migrations setup
- Free Tier Redis via Upstash setup instructions

## 🚀 Example: The ultimate Node/Express Dockerfile

Looking to dockerize a Node app? Just copy this:

```dockerfile
# Build stage
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Production stage
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app/package*.json ./
COPY --from=builder /app/dist ./dist
RUN npm ci --only=production
USER node
EXPOSE 3000
CMD ["node", "dist/index.js"]
```

Check out the `/docker/node` directory for the accompanying `docker-compose.yml` to pair with this Dockerfile.

## ⚙️ Automated CI/CD (GitHub Actions)

We also provide plug-and-play `.github/workflows` to automate your deployments. 
See the `/github-actions` directory for:
- Auto-deploy to AWS ECS on `main` push
- Vercel preview environments for PRs
- Automated test runners

## 🤝 Contributing

Got a rock-solid deployment config that isn't listed here? We'd love your contribution! Please see our `CONTRIBUTING.md` guidelines.

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
*Maintained with ❤️ by Ahmar Hussain and [Stackaura](https://www.stackaura.com/). Let's make deployment painless.*
