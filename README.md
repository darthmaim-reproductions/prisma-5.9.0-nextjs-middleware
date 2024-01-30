# https://github.com/prisma/prisma/issues/22877

This is a repository to reproduce the error introduced by prisma@5.9.0 in combination with Next.js middleware.

## Reproduction

Follow these steps to reproduce the issue:

 1. Clone this repo
 2. Run `npm install` to install dependencies
 3. Run `npx prisma generate` to generate prisma client
 4. Run `npm run dev` to start Next.js dev server
 5. Visit http://localhost:3000/ in your browser to trigger middleware ([middleware.ts](/middleware.ts))
 6. Observe error in terminal and error overlay
    ```
     ⨯ middleware.ts (4:23) @ ModelName
     ⨯ Cannot read properties of undefined (reading 'ModelName')
      2 |
      3 | export default function() {
    > 4 |     console.log(Prisma.ModelName.User)
        |                       ^
      5 | }
    ```

## How this repo was created

 1. Based on default Next.js template `reproduction-template`
 2. Installed prisma according to https://www.prisma.io/docs/getting-started/quickstart
 3. Added a Next.js middleware
