FROM node AS base
WORKDIR /app

# install npm dependencies and build

COPY package.json /app/
COPY package-lock.json /app/

RUN npm install

COPY ./ /app

RUN npm run build --production

RUN npm install -g serve


# add third-party licenses so this image may be distributed

FROM base AS licenses
WORKDIR /app

ADD https://raw.githubusercontent.com/xronos-inc/node-third-party-licenses/refs/tags/v1.0.0/third-party-licenses.js /app/
RUN npm install license-checker
RUN npx license-checker --production --json > licenses.json
RUN node third-party-licenses.js licenses.json


# application stage

FROM base AS application
WORKDIR /app

COPY --from=licenses /app/THIRD_PARTY_LICENSES.md /app/
COPY --from=licenses /app/third-party-licenses /app/third-party-licenses

ENTRYPOINT ["serve", "-s", "build"]

EXPOSE 3000
