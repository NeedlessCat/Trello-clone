This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

---

--------------------- LECTURE-1 ---------------------
--> npx create-next-app@latest trello-tutorial
--> npx shadcn-ui@latest init

- we will get 'components' and 'lib' folders
- 'lib' contains 'utils.ts' which has "cn" in its code.(helpful to combine different tailwind classes.)

--------------------- LECTURE-2 ---------------------
--> Creating different route pages.
--> Here next.js provides a way to get different pages for different users.
This is done by a dynamic page(named as "[...]").

--> example page is accessed as "localhost:3001/example".
id page is accessed as "localhost:3001/users/1293"
(since [id] is dynamic, it can has 123, 1456 etc)

--> we can create a folder named "(...)"

- It helps to create a folder that can't be Routed.
- It helps to make a seperate collections of template files/folders.
  (Inside (test)-folder, create something-folder with page.tsx)
- It also helps to set different layout for some particular set of pages.

- We can create API routes as well...
  Example:
  import { NextResponse } from "next/server";
  export function GET() {
  return NextResponse.json({
  hello: "trello",
  });
  };

      export function POST() {
          return NextResponse.json({
              hello: "trello",
          });
      };

      export function PATCH() {
          return NextResponse.json({
              hello: "trello",
          });
      };

  --------------------- LECTURE-3 ---------------------

--------------------- LECTURE-4 ---------------------
Now, starting with our PROJECT Creation...
--> we remove the 'page.tsx'.
--> create (marketing) folder containing pag.tsx
{indicating it as a marketing page}
--> Added some content in the page with designs and responsiveness
--> npx shadcn-ui@latest add button
(It will generate 'button.tsx' in components/ui)
--> Import the 'Button' and 'link' into the markertingPage and use it for their purposes.

--> we learnt to import font as...
a) import localFont from "next/font/local"
b) const headingFont = localFont({
src : "../../ ......."
});
c) import {cn} from "@/lib/utils";
d) get all class-styles inside 'cn' and add font as..

<div className={cn(
    "flex items-center justify-center flex-col",
    headingFont.className,
)}>
--> we can add google font as well..
   (see the example for "Poppins")

--> Now designed the logo in 'logo.jsx'
--> anothor type of folder, whose files are only visible when included/imported in the code.
named as "\_foldername".
--------------------- LECTURE-5 ---------------------
--> After impleamenting Navbar, Footer, metadata and all..
We are set to create Sign In/ Sign Up page...
--> For this, we will be using 'Clerk'
--> One thing we do is not clear to me, please look over it once again , ie,
(We added '.env' in '.gitignore' file).
It says, it is for prisma and all...

--------------------- LECTURE-6 ---------------------
--> Now working over the protected page.
(A page where we get transmitted after logged in)
--> Here, we can access logged_in persons details via clerk.
--> For this, we would be using some hooks like 'useAuth', 'useUser' etc,
so we need to be in client side (not server side).

-------------------**\*\***\_\_\_**\*\***

It was just for the knowlegdge...
so deleted the protected page..
"use client";

//import {useAuth, useUser} from "@clerk/nextjs";
import {UserButton} from "@clerk/nextjs";

const ProtectedPage = () => {
//const { userId } = useAuth();
//const { user } = useUser();

    return (
        // <div>
        //     User {user?.firstName}
        //     userId: {userId}
        // </div>
        <div>
            <UserButton afterSignOutUrl="/"/>
        </div>
    );

};

export default ProtectedPage;

--------------------- LECTURE-7 ---------------------
--> We created the organization page.
--> we have taken care of the page transitions like..
a) A person needs to sign in first.
b) Then must have an organization.
c) Then he can work over the main pageflow.
--> We also taken care of the issue like..
a) Changing organization changes the url but
changing the url not changes the organization.

Now,

(installing stuffs to create the sidebar)
--> npm i usehooks-ts
--> npx shadcn-ui@latest add skeleton
(add skeleton.jsx in component/ui)
--> npx shadcn-ui@latest add accordion
--> npx shadcn-ui@latest add separator

--------------------- LECTURE-8 ---------------------
Creating sidebar is a bit complicated...
Go through it once again and again..

---

For creating mobile sidebar, we install..
--> npm i zustand
--> npx shadcn-ui@latest add sheet
Then we create a folder 'hooks' to control opening and closing of the sidebar in mobile.

---

One thing to learn..
= (set) => { return..} --> creates a function..
= (set) => ({...}) --> automatically returns null.

---

One more thing to learn...
"use client" section is also rendered in the server-side.
And to get sth is on server-side or client-side, we use 'useEffect' (it doesn't run on server-side)
useEffect(() => {
setIsmounted(true);
}, []);

if(!isMounted) {
return null;
}

--------------------- LECTURE-9 ---------------------
Now we are finished with the designing section for now...
Starting to work on Database using prisma...
--> npm i -D prisma
--> npx prisma init

Then we set the Supabase and go for adding models.
--> add 'model board' to the schema.prisma
--> npx prisma generate
--> npx prisma db push
--> npm i @prisma/client
--> npm run dev
--------------------- LECTURE-10 --------------------

--------------------- LECTURE-11 --------------------

--------------------- LECTURE-12 --------------------

--------------------- LECTURE-13 --------------------
