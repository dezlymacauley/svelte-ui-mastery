# UI Design Setup
_______________________________________________________________________________

Create the directory
```sh
mkdir ui-design
```
_______________________________________________________________________________

Enter the directory
```sh
cd ui-design
```

For the rest of this guide, 
all commands should be run from the root of this directory.

_______________________________________________________________________________

Use this command to view the list of Deno versions that you can download, 
then run this command:
```sh
mise ls-remote deno
```

If you simply want to know what is the latest stable version of Deno,
use this command: 
```sh
mise latest deno
```
_______________________________________________________________________________

This is how you set a specific version of Deno in your project
```sh
mise use deno@2.6.8
```

You should now have a `mise.toml` file that looks like this:
```toml
[tools]
deno = "2.6.8"
node = "25.6.0"
```
_______________________________________________________________________________

I like to have my language servers installed locally and 
because language servers assume you have `Node.js` installed 
I will need to install Node.js locally using mise.

```sh
mise use node@25.6.0
```
_______________________________________________________________________________

Install the `dx` alias for Deno. This is Deno's equivalent of the npx 
command in Node.js.
```sh
deno x --install-alias
```
_______________________________________________________________________________

Run the Svelte CLI with this command:
```sh
dx sv create .
```

If you are running this command for the first time,
you may see a message like this:
```
Install npm:sv? [Y/n]
```

Type `Y` and press enter.

_______________________________________________________________________________

Selected `Yes`. 

The reason the directory is not empty is because of the `mise.toml` file 

```
┌  Welcome to the Svelte CLI! (v0.11.4)
│
◆  Directory not empty. Continue?
│  ● Yes / ○ No
└
```
_______________________________________________________________________________

I selected `SvelteKit minimal` so that I have a barebones project with 
less things to delete after the project is created.
```
◆  Which template would you like?
│  ● SvelteKit minimal (barebones scaffolding for your new app)
│  ○ SvelteKit demo
│  ○ Svelte library
└
```
_______________________________________________________________________________

I always use `TypeScript` because Deno has first-class support for it.
```
◆  Add type checking with TypeScript?
│  ● Yes, using TypeScript syntax
│  ○ Yes, using JavaScript with JSDoc comments
│  ○ No
└
```
_______________________________________________________________________________

Use the spacebar to select `tailwindcss` then press enter
```
◆  What would you like to add to your project? (use arrow keys / space bar)
```

Use the arrow keys to find this option, then press the `spacebar` to 
select it, and then press `Enter` to continue
```
◼ tailwindcss (css framework - https://tailwindcss.com)
```
_______________________________________________________________________________

Press `Enter` to proceed without selecting any plugins.
```
◆  Which plugins would you like to add?
│  ◻ typography (@tailwindcss/typography)
│  ◻ forms
└
```
_______________________________________________________________________________

Use the arrow keys to select `deno` then press `Enter`

```
◆  Which package manager do you want to install dependencies with?
│  ○ None
│  ○ npm
│  ○ yarn
│  ○ pnpm
│  ○ bun
│  ● deno
└
```
_______________________________________________________________________________

Add language support for Svelte as a dev dependency
```sh
deno add -D npm:svelte-language-server@latest
```
_______________________________________________________________________________

Add language support for files with Tailwind CSS classes, as a dev dependency
```sh
deno add -D npm:@tailwindcss/language-server@latest
```
_______________________________________________________________________________

Add language support CSS, HTML, and JSON files.
```sh
deno add -D npm:vscode-langservers-extracted@latest
```

You'll get this warning because Deno prevents npm packages from automatically
installing post install scripts:
```
╭ Warning
│
│  Ignored build scripts for packages:
│  npm:core-js@3.48.0
│
│  Run "deno approve-scripts" to run build scripts.
╰─
```

Run the command:
```sh
deno approve-scripts
```

You'll get a menu like this. Use the arrow keys and the spacebar to select,
these scripts, then press Enter.
```
? Select which packages to approve lifecycle scripts for (<space> to select, ↑/↓/j/k to
navigate, a to select all, i to invert selection, enter to accept, <Ctrl-c> to cancel)
  ● npm:core-js@3.48.0
❯ ● npm:esbuild@0.27.2
```

You should see a message like this if you have `Node.js` installed.
```
Approved npm:core-js@3.48.0
Approved npm:esbuild@0.27.2
Ran build script npm:core-js@3.48.0
Ran build script npm:esbuild@0.27.2
```
_______________________________________________________________________________

Add language support for TypeScript.
Don't use Deno's built-in lsp in SvelteKit projects as you will 
get false warnings. As a matter of fact, the denolsp will deliberately 
disable itself when it detects a `package.json` file in your project, 
to avoid a clashing with the TypeScript language server.
```sh
deno add -D npm:typescript-language-server@latest
```
_______________________________________________________________________________

Add the deno adapter as a dev dependency, 
to ensure that when you build your application,
it is optimized for deployment on the platform `Deno Deploy`
```sh
deno add -D npm:@deno/svelte-adapter@latest
```
_______________________________________________________________________________

Add GSAP animations as a project dependency (Not a dev dependency):
```sh
deno add npm:gsap@latest
```
_______________________________________________________________________________

When starting a new project I recommend running this once:
```sh
deno outdated
```
_______________________________________________________________________________

Then updating with this
```sh
deno update --latest
```
_______________________________________________________________________________

Delete the `.vscode` directory
```sh
rm -rf .vscode
```
_______________________________________________________________________________

Delete `src/lib/index.ts`
```sh
rm src/lib/index.ts
```
_______________________________________________________________________________

Clear the contents of `src/routes/+layout.svelte`
```sh
truncate -s 0 src/routes/+layout.svelte
```

Replace the contents with this:
```svelte
<script lang="ts">
  let { children } = $props();
</script>

{@render children()}
```
_______________________________________________________________________________

Rename `src/lib/assets/favicon.svg` to:

`src/lib/assets/svelte_logo.svg`
_______________________________________________________________________________

Clear the contents of the home page
```sh
truncate -s 0 src/routes/+page.svelte
```

Replace the contents of the page with this:
```svelte
<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
```

I want to have full control over the `+page.svelte` of each route. 
_______________________________________________________________________________

Delete `src/routes/layout.css`
```sh
rm src/routes/layout.css
```

Normally you'd want to keep this, 
but I want each route in my SvelteKit project to be a mini web page with its
own layout.
_______________________________________________________________________________

Open `src/routes/+layout.svelte`

```svelte
<script lang="ts">
  import "./layout.css";
  import favicon from "$lib/assets/favicon.svg";

  let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
{@render children()}
```

Delete this line:
```
import "./layout.css";
```
_______________________________________________________________________________

Clear the contents of the README page
```sh
truncate -s 0 README.md
```
_______________________________________________________________________________

Clear the contents of the .gitignore file
```sh
truncate -s 0 .gitignore
```

Add this to the `.gitignore` file:
```gitignore
# Build outputs (Deno, Vite, SvelteKit)
.deno-deploy/
.svelte-kit/

# Project dependencies (npm)
node_modules/
```
_______________________________________________________________________________

Create a deno.json file (if one already exists, nothing will happen)
```sh
touch deno.json
```

You should already have a `deno.json` file that contains the following,
because of the `deno approve-scripts` command that was run earlier
```json
{
  "allowScripts": ["npm:core-js@3.48.0", "npm:esbuild@0.27.2"]
}
```
_______________________________________________________________________________

Add this to the file so that Deno's built-in formatter 
can format Svelte code.
```
"unstable": ["fmt-component"]
```

So the final `deno.json` should look like this:
```json
{
  "allowScripts": ["npm:core-js@3.48.0", "npm:esbuild@0.27.2"],
  "unstable": ["fmt-component"]
}
```
_______________________________________________________________________________

Go to the scripts section of the `package.json` file
```json
	"scripts": {
		"dev": "vite dev",
		"build": "vite build",
		"preview": "vite preview",
		"prepare": "svelte-kit sync || echo ''",
		"check": "svelte-kit sync && svelte-check --tsconfig ./tsconfig.json",
		"check:watch": "svelte-kit sync && svelte-check --tsconfig ./tsconfig.json --watch"
	},
```
_______________________________________________________________________________

Replace it with this:
```json
	"scripts": {
		"dev": "vite dev --open --port 6969",
        "build": "deno task prepare && vite build",
		"preview": "vite preview --open --port 6969",
		"prepare": "svelte-kit sync || echo ''",
		"check": "svelte-kit sync && svelte-check --tsconfig ./tsconfig.json",
		"check:watch": "svelte-kit sync && svelte-check --tsconfig ./tsconfig.json --watch",
        "clean": "rm -rf .svelte-kit .deno-deploy node_modules",
        "setup": "deno task clean && deno install && deno task prepare && deno task build"
	},
```
_______________________________________________________________________________

Go to the `devDependenies` section of package.json

Deleting the line `@sveltejs/adapter-auto`

This is the default adapter.

_______________________________________________________________________________

Remove all the `^` in the entire `package.json` file:

E.g. Change this:
`"@deno/svelte-adapter": "^0.1.0",` 

to this:
`"@deno/svelte-adapter": "0.1.0",` 

This will make the project highly reproducible

_______________________________________________________________________________

Open svelte.config.json

Delete this line
```sh
import adapter from '@sveltejs/adapter-auto';
```

Replace it with:
```sh
import adapter from "@deno/svelte-adapter";
```

You can also clean up all the comments, except for the type definition,
so your `svelte.config.js` file should look like this:
```js
import adapter from "@deno/svelte-adapter";
import { vitePreprocess } from "@sveltejs/vite-plugin-svelte";

/** @type {import('@sveltejs/kit').Config} */
const config = {
  preprocess: vitePreprocess(),
  kit: {
   adapter: adapter(),
  },
};

export default config;
```
_______________________________________________________________________________

To view a list of the available commands in your `package.json` file,
then run this command:

```sh
deno task
```
_______________________________________________________________________________

This this will prepare any changes that were made in the 
the `svelte.config.js` file.
```sh
deno task prepare
```
Whenever you have made changes to your `svelte.config.js`,
you always want to run this command afterwards so that SvelteKit can build
your project with these new settings.
_______________________________________________________________________________

Check that your project can be built successfully.
```sh
deno task build
```
_______________________________________________________________________________

View the production build of your project.
```sh
deno task preview
```

Press `Ctrl + c` to close the server when you are done.
_______________________________________________________________________________

Check that the SvelteKit check commands are working

```sh
deno task check
```
_______________________________________________________________________________

```sh
deno task check:watch
```

Press `Ctrl + c` to close the server when you are done.

_______________________________________________________________________________

Whenever you are not going to be working your project for a long
while, you can run this command to save on disk space:
```sh
deno task clean
```

This command is also quite usefull if you want to re-install dependencies.

_______________________________________________________________________________

When you want to work on your project again, 
run these commands and it will be built up the same way.

First give mise permission to execute the instructons in the mise.toml file
```sh
mise trust
```

Then install the project dependencies with Deno
```sh
deno install
```

Now that you have Deno in your project, you can run the `setup` script.
```sh
deno task setup
```
_______________________________________________________________________________

To check that hot reloading is working, 
open your project in a separate terminal and run this:
```sh
deno task dev
```

Then open the following page, type some letters, 
save and check if they appear in the html file.
```sh
src/routes/+page.svelte
```
_______________________________________________________________________________
