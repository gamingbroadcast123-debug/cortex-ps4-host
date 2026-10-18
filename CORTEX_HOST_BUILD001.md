# CORTEX HOST // PS4 — UI Build 001

Standalone browser launcher inspired by the CORTEX OS visual language. Target testing platform: PlayStation 4 firmware 9.00.

## Important separation

- `src/launcher.html` is the custom landing page and does **not** execute the exploit automatically.
- `src/index.html` is the **unchanged upstream** PSFree-Lapse exploit entrypoint. Clicking **ENTER EXPLOIT** navigates to it.
- PSFree-Lapse reports PS4 7.00–9.60 as supported for the current chain, but this fork's modifications have **not yet been tested on a PS4**.
- Payload management / GoldHEN delivery is **not integrated** in this build. The UI does not assert a payload has been loaded.
- This project is separate from the Harvest the Cortex game and CORTEX OS software.

## Local preview (Windows)

In a terminal:

```powershell
git clone https://github.com/gamingbroadcast123-debug/cortex-ps4-host.git
cd cortex-ps4-host
git switch feature/cortex-host-ui-001
cd src
py -3 -m http.server 8088 --bind 127.0.0.1
```

Open `http://127.0.0.1:8088/launcher.html` in your PC browser.

**Warning:** Do not click ENTER EXPLOIT from a normal PC browser. The original exploit entrypoint targets PlayStation browsers; a desktop browser is suitable for previewing this launcher UI only.

## PS4 smoke test checklist

1. Verify the title, animation, and three launcher panels fit the PS4 browser viewport.
2. Verify the console and firmware labels correctly detect the actual browser user-agent; do not interpret browser detection as an exploit success.
3. Check navigation using the controller's browser mappings; keyboard arrow keys and Enter are wired for desktop testing, but PS4 controller events remain unverified.
4. Verify that the upstream entrypoint is unchanged relative to `main`.
5. Test exploit execution only after configuring a compatible, trusted local host and understanding the risk of console crashes.
6. Avoid exposing the host outside your home network or adding unverified payload sources.

## Licensing and credit

The upstream project is [Al-Azif/psfree-lapse](https://github.com/Al-Azif/psfree-lapse), licensed AGPL-3.0-or-later. Preserve upstream authorship and license notices. This new UI is contributed as part of the same fork under the repository's AGPL terms.
