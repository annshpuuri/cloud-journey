## Task: Serve a custom page with nginx
**Commands used**
- `sudo cp ... ~/index.backup.html`: backup before editing
- `sudo nano /var/www/html/index.html`: created the page
- `sudo nginx -t`: config check
- `sudo systemctl restart nginx`: apply

**Error:** curl: (7) Failed to connect to localhost port 80
**Cause:** I started ssh instead of nginx
**Fix:** `sudo systemctl start nginx`, verified with `curl -I localhost`

**Error:** nginx failed after my edit (deliberate test)
**Cause:** missing semicolon in the site config
**Fix:** `nginx -t` pointed to the line; restored the backup

**Lesson:** always run `nginx -t` before restarting, and back up before editing.
