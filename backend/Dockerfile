# backend/Dockerfile (multi-stage)
# Builder stage (install deps)
FROM node:18-alpine AS deps
WORKDIR /app
COPY package*.json ./
RUN npm ci --production

# Optional builder if you need to compile assets (TypeScript etc)
FROM node:18-alpine AS builder
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .
# If using TypeScript: RUN npm run build
# If not, this just prepares the app
RUN ls -la

# Runtime stage (small, non-root)
FROM node:18-alpine AS runner
WORKDIR /app
ENV NODE_ENV=production
COPY --from=builder /app ./
# create non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser
EXPOSE 3000
CMD ["node", "server.js"]  # change to your start file or npm start
