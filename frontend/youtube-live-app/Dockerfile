FROM node:18-alpine3.17 as build
WORKDIR /app
COPY package*.json ./
RUN npm ci --silent
COPY . .
RUN npm run build

FROM build AS runner
WORKDIR /app
COPY --from=build /app/.next ./
COPY --from=build /app/package*.json ./

EXPOSE 3000
CMD ["npm", "start"]