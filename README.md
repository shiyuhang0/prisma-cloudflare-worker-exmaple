# Run TiDB Serverless with Prisma on Cloudflare Worker

This repo is an example of how to run TiDB Serverless with Prisma on Cloudflare Worker.

## How to run this example

### Prerequisites

Before running through the following steps, make sure you have:

1. Node.js installed on your machine
2. a Cloudflare account
3. a TiDB Serverless instance up and running and its connection string available

### 1. Database URL setup

Create a `.env` file in the root of the project with the following content. You can get the connection string from the TiDB Serverless console.

```env
DATABASE_URL="mysql://<user>:<password>@<host>:4000/<database>?sslaccept=strict"
```

In the wrangler.toml file, add the following environment variable:

```toml
[vars]
DATABASE_URL = "mysql://<user>:<password>@<host>:4000/<database>?sslaccept=strict"
```

### 2. Install dependencies

```
npm install
```

### 3. Sync the database schema

```
npx prisma db push
```

### 4. Run on Local

```
npm run dev
```

### 5. Deploy to Cloudflare Worker

```
npm run deploy
```

## How this example built

1. Initialize project: `npm create cloudflare@latest prisma-cloudflare-worker-example -- --type hello-world`
2. Set up prisma: `cd prisma-cloudflare-worker-example` and `npm install --save-dev prisma`
3. Init prisma: `npx prisma init --datasource-provider mysql`
4. update .env file: `DATABASE_URL=mysql://<user>:<password>@<host>:4000/<database>?sslaccept=strict`
5. update schema.prisma file as this example
6. sync db schema: `npx prisma db push`
7. update wrangler.toml file as this example
8. install dependencies: `npm install @tidbcloud/prisma-adapter @tidbcloud/serverless`
9. update src/index.js file as this example



