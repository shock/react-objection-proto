`<repo_root>/server` is the root directory for the express.js server.  It is a full-blown backend server with database
persistence using the objection.js and knex.js libraries.

Database configuration is in src/db
Objection models are in src/models

A softlink in src/client_server is made to the root src/client_server to share Typescript types as a convenience.

Run `yarn console` to start a REPL console capable of running ad-hoc DB queries.  See `console.ts` for more info.

### Notes

The main reason for creating the server in it's own virtual root directory was to get around the limitations of
using create-react-app without ejecting it.  Certain limitations on Typescript configuration in `tsconfig.json`
couldn't be worked around without ejecting, which I didn't want to do to keep deployment more straight-forward,
and keep the React dev environment consistent with a vanilla CRA app.

Additionally, there were complications with setting up Jest in the server code without having to eject CRA.
Having a separate jest config worked around that.  There are still complications with running the server using
the VSCode debugger.  Need to test different .vscode launch configs, perhaps launching using `tsnode` instead
of `node`.  Need to do more research there.

Finally, I wanted to keep the client and server as separate logical concerns with having to maintain two distinct
repositories.  In VSCode, I hide the server directory in the client workspace and start a separate workspace
with the `/server` as the root directory, so I treat them as two logically separate projects.

I haven't actually deployed this setup yet, so it remains to be seen what the complexity will be, but the hope
is that even on something like Heroku, it's as simple and building both client and server, then starting just
the server process as described in the root README.