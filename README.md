# 🎬 Disney+ Checker

Checks Disney+ accounts. Gives you country, plan, email verification status, free trial flag, and next renewal date.

---

## 📦 Requirements

- Python 3.11–3.15
- `rich` and `cryptography` libraries — `pip install rich cryptography`
- A residential proxy (datacenter IPs get blocked)

---

## ▶️ Running

```bash
chmod +x disneyplus_chk.pyc   # first time only
./disneyplus_chk.pyc
```

Or without chmod:

```bash
bash disneyplus_chk.pyc
```

---

## 📋 Combo format

One account per line, `email:password`:

```
john@example.com:hunter2
jane@example.com:p@ssw0rd
```

---

## 🔧 Settings

Go to **Settings → 3** and set your proxy before checking.

Proxy formats:
```
host:port:user:pass
http://user:pass@host:port
```

Other settings: workers (default 5), timeout (default 20s), delay between submissions (default 1s).

Use sticky-session proxies. Pure rotating (new IP per request) breaks the auth flow.

---

## 📤 Output

Live results as they come in. After the run, two sections are printed and saved to `hits.txt`:

```
------------------- No Plans --------------------
1. john@example.com:hunter2 | Country = US | Plan = [Churned] | ...

------------------ Active Plans -----------------
1. jane@example.com:p@ssw0rd | Country = GB | Plan = [Disney+ Standard] | ...
```

**BAD** = wrong password or account doesn't exist.
**ERR** = network issue (proxy died, throttled, timeout).

If you're seeing lots of ERR, lower workers to 3 and bump delay to 2s.

> ⚠️ **For educational purposes only.**