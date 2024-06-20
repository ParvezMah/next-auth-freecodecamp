


> 42:19 / 1:26:54 - Protecting Pages - Client Side Page
```
    Bug : Async / Await is supported on client componet
    Debug : 
        import { useSession } from "next-auth/react";
        import { redirect } from "next/dist/server/api-utils";
        const { data: session } = useSession({
            required: true,
            onUnauthenticated() {
            redirect("/api/auth/signin?callbackUrl=/clientMember");
            },
        });

        Error: [next-auth]: `useSession` must be wrapped in a <SessionProvider />

        1. Created (components)>AuthProvider
            "use client"

            import { SessionProvider } from "next-auth/react"

            const AuthProvider = ({children}) => {
                return <SessionProvider> {children} </SessionProvider>
            }

            export default AuthProvider;
        2. then wrapped full body into it
            const RootLayout = ({ children }) => {
                return (
                    <html lang="en">
                    <AuthProvider>
                        <body className="bg-gray-100">
                        <Nav/>
                        <div className="m-2">
                            {children}
                        </div> 
                        </body>
                    </AuthProvider>
                    </html>
                );
            }

```