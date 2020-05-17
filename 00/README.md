# example (app.ts)

```bash
user@DESKTOP-9VVBDPS MINGW64 /d/110713305/learn_Deno/00 (master)
$ deno run app.ts
error: Uncaught PermissionDenied: network access to "0.0.0.0:8000", run again 
with the --allow-net flag
    at unwrapResponse ($deno$/ops/dispatch_json.ts:43:11)
    at Object.sendSync ($deno$/ops/dispatch_json.ts:72:10)
    at Object.listen ($deno$/ops/net.ts:51:10)
    at listen ($deno$/net.ts:152:22)
    at serve (https://deno.land/std/http/server.ts:261:20)
    at file:///D:/110713305/learn_Deno/00/app.ts:2:11

user@DESKTOP-9VVBDPS MINGW64 /d/110713305/learn_Deno/00 (master)
$ deno run --allow-net  app.ts
http://localhost:8000/
```

* We have a permission denied problem.

    if a program want to access the network like in the previous case, then we need to give it permission.

    We can do so by passing a flag when we run the command, in this case `--allow-net`

# Formatting code

格式化 Deno 的程式碼

`deno fmt app.ts`

# example (cat.ts)

```bash
user@DESKTOP-9VVBDPS MINGW64 /d/110713305/learn_Deno/00 (master)
$ deno run https://deno.land/std/examples/cat.ts

user@DESKTOP-9VVBDPS MINGW64 /d/110713305/learn_Deno/00 (master)
$ deno run --reload https://deno.land/std/examples/cat.ts
Download https://deno.land/std/examples/cat.ts
Warning Implicitly using master branch https://deno.land/std/examples/cat.ts
Compile https://deno.land/std/examples/cat.ts

user@DESKTOP-9VVBDPS MINGW64 /d/110713305/learn_Deno/00 (master)
$ deno run https://deno.land/std/examples/cat.ts

user@DESKTOP-9VVBDPS MINGW64 /d/110713305/learn_Deno/00 (master)
$ deno run https://deno.land/std/examples/cat.ts app.ts
error: Uncaught PermissionDenied: read access to "D:\110713305\learn_Deno\00\app.ts", run again with the --allow-read flag
    at unwrapResponse ($deno$/ops/dispatch_json.ts:43:11)
    at Object.sendAsync ($deno$/ops/dispatch_json.ts:98:10)
    at async Object.open ($deno$/files.ts:37:15)
    at async https://deno.land/std/examples/cat.ts:4:16

user@DESKTOP-9VVBDPS MINGW64 /d/110713305/learn_Deno/00 (master)
$ deno run --allow-read=./ https://deno.land/std/examples/cat.ts app.ts
import { serve } from "https://deno.land/std/http/server.ts";

const s = serve({ port: 8000 });
console.log("http://localhost:8000/");

for await (const req of s) {
  req.respond({ body: "Hello World\n" });
}
```

