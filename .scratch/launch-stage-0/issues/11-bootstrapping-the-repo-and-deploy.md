# Ticket: How does an empty VPS become a served site?

Type: task
Status: open
Blocked by: 01, 09

## Question

What are the exact steps, in order, to go from an empty `~/code/blog/gudangtool` to `https://gudangtool.web.id` serving a built site, and what must exist on the VPS before the first automated deploy can work?

## Detail

`14-repo-spec.md` §11 specifies the deploy: Actions → rsync → symlink swap → 3 releases kept → Cloudflare purge. `12-tech-stack.md` §9 adds a 6-hour cron rebuild.

None of that can run until some one-time state exists. This ticket is the checklist for that state — it does not decide anything, it does a thing that unblocks every deploy ticket.

Known facts: `sumojak` reachable, Caddy installed at `/usr/bin/caddy`, 2 vCPU / 1.9 GB. `sumoclaw` down.

The checklist must cover:

1. Create the git repo in `~/code/blog/gudangtool`, initial commit of existing `docs/` (with `.DS_Store` removed, or `.gitignore` it).
2. GitHub repo `fanioz/gudangtool` — private (launch-plan §6 #3 recommends private while content is unready).
3. SSH key / deploy user on `sumojak`; does root SSH in as root or should a `deploy` user exist?
4. Directory `/var/www/gudangtool/{releases,current}` and permissions.
5. Caddyfile skeleton with the domain, root `current/`, headers from `14-repo-spec.md` §12. Not yet serving — no release exists.
6. GitHub Actions secrets: SSH host, user, key, target path.
7. Cloudflare zone for `gudangtool.web.id` — verify nameserver change is possible for `.web.id`.

Resolved when: a placeholder `index.html` is reachable at the domain over HTTPS, and a test commit on `main` replaces it via CI.
