# ============================================================
# STAGE 1: BUILD REACT APPLICATION
# ============================================================

FROM node:24-alpine AS build

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build


# ============================================================
# STAGE 2: SERVE REACT APPLICATION
# ============================================================

FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]