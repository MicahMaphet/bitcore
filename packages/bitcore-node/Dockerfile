FROM node:22

# initial setup
RUN set -x && node -v && npm -v
WORKDIR /bitcore

# Add source
# NOTE(danny): not the most optimal layering, but it works for now
COPY lerna.json ./
COPY package*.json ./
COPY packages/ ./packages/

# Install dependencies and build
RUN npm install --ignore-scripts
RUN npm run bootstrap
RUN npm run compile

# Start the server
CMD ["node", "packages/bitcore-node/build/src/server.js"]