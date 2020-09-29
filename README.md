# Quasar App Extension dotenv

Fork of the `@quasar/dotenv` project to support artibrarty env files, not bound to `NODE_ENV`.

Example usage:

```
TARGET=foo quasar build  # build using `foo.env`
TARGET=dev quasar build  # build using `dev.env`
TARGET=prod quasar dev   # start dev server using `prod.env`
```

Invoking a quasar command without specifying a `TARGET` reverts to default behavior, using the appropriate `NODE_ENV` env file.

Additionally, our fork allows for overriding values set via .env files via command-line args. eg: `FOO=false TARGER=dev quasar develop` sets `process.env.FOO` to false, even if .env specifies `FOO=true`

# Install

```bash
quasar ext add @quasar/dotenv
```

Quasar CLI will retrieve it from NPM and install the extension.

## Prompts

1. "What is the name of your .env that you will be using for development builds?"
   The default is ".env"

2. "What name would you like to use for your Common Root Object ('none' means to not use one)?"
   The default is "none"
   The "common root object" means off of "process.env" you will have a named object, basically for organization purposes.

3. "Create your .env files for you?"
   The default is "true" (yes)
   If you say "yes" to this question, then your .env files will be automatically created for you.

4. "For security, would you like your .env files automatically added to .gitignore?"
   The default is "true" (yes)
   If you say "yes" to this question, then your .env files will automatically be inserted into the .gitignore.
   For security purposes, because you may have sensitive data in your .env file, you should not keep it in a repository.

Any data in a `.env` will be placed in `process.env` at the browser level.

If you specified a common root object, say `MyData`, then the data will be placed at `process.env.MyData`.

Be aware, if you have something like this in your `.env`:

`APP_PORT=4000`

Then you will need to use the `parseInt()` function as it will be propogated to the browser code as a string.

# Uninstall

```bash
quasar ext remove @quasar/dotenv
```

# Donate

If you appreciate the work that went into this, please consider donating to [Quasar](https://donate.quasar.dev) or [Jeff](https://github.com/sponsors/hawkeye64).

# License

MIT (c) Jeff Galbraith <jeff@quasar.dev>
