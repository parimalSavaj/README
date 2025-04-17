# 1️⃣ Base Image
FROM node:18

# 2️⃣ Working Directory Set Karo
WORKDIR /app

# 3️⃣ Dependencies Copy Karo
COPY package.json package-lock.json ./
RUN npm install

# 4️⃣ Source Code Copy Karo
COPY . .

# 5️⃣ Port Expose Karo
EXPOSE 3000

# 6️⃣ Default Command Run Karo
CMD ["node", "server.js"]
