===============================================================
  
  DEBT TRACKERS  —  Student Loan Payoff Tools
  
===============================================================

Two self-contained, single-file web apps for tracking and
gamifying student-loan payoff. Each is one HTML file — no build
step, no dependencies, no server. Open it in a browser and go.

  • loan-payoff-tracker_RPG.html    -> "Debt Slayer" (boss-battle theme)
  • loan-payoff-tracker_Garden.html -> "Grove Keeper" (plant/mushroom theme)

Both share the same engine; only the theme and the loaded loans
differ.


---------------------------------------------------------------
 WHAT THEY DO
---------------------------------------------------------------
  - Track each loan and its remaining balance.
  - Use the AVALANCHE strategy: always attack/tend the highest
    interest-rate loan first (saves the most money).
  - Log each payment ("payday") and auto-allocate it to the
    right loan, then show exactly what to type into your loan
    servicer's per-loan payment screen.
  - Estimate daily interest accrual between visits so balances
    stay lifelike (unsubsidized loans only; subsidized loans in
    forbearance are treated as dormant / not growing).
  - A what-if slider projects paydays / months to payoff.
  - Celebrations when a loan is cleared and when you finish.
  - Cloud save + cross-device sync via JSONBin (optional).
  - Local autosave + Backup/Restore as a fallback.


---------------------------------------------------------------
 DEPLOY (GitHub Pages)
---------------------------------------------------------------
  1. Put the HTML file(s) in the repo.
  2. Repo -> Settings -> Pages -> Deploy from branch
     (branch: main, folder: / root). Save.
  3. Wait ~1 minute. Your URL will be:
       https://<username>.github.io/<repo>/loan-payoff-tracker_RPG.html
  4. Bookmark it on each device.

  NOTE ON CACHING: After re-uploading an updated file, do a HARD
  refresh (Ctrl+Shift+R on desktop; fully close/reopen the tab on
  mobile) or you may keep seeing the old cached version. Each file
  shows a small build tag at the bottom of the page so you can
  confirm the new version is live.

  RENAMING: You can rename the HTML file freely — nothing breaks.
  The URL changes (update your bookmark); saved progress stays
  because the browser ties data to the SITE, not the filename.


---------------------------------------------------------------
 CLOUD SYNC (JSONBin) — optional but recommended
---------------------------------------------------------------
  Local-only works fine on one device. For sync across phone +
  desktop:

  1. Make a free account at jsonbin.io and copy your MASTER KEY.
  2. Open the tracker -> "Cloud Save & Sync" -> expand setup.
  3. Paste the Master Key, LEAVE BIN ID BLANK, click
     "Connect / Create". It creates a private bin and shows you
     a BIN ID.
  4. SAVE THAT BIN ID. On every other device, paste the SAME
     Master Key + the SAME Bin ID, then click Connect.
  5. After that it auto-saves on every change and pulls the
     latest when you open it.

  IMPORTANT:
   - One Master Key can run many trackers — just give EACH
     tracker its OWN separate Bin ID (blank on first connect).
     Reusing a Bin ID across two trackers will overwrite data.
   - Keys are stored only in your browser (a separate local slot)
     and are NEVER written into the cloud save.
   - Free-tier request limits are far beyond what these tools
     use; a few updates a month is negligible.


---------------------------------------------------------------
 DATA, BACKUP & SAFETY
---------------------------------------------------------------
  - Progress is saved automatically in the browser (localStorage),
    keyed PER TOOL so the two trackers never collide even on the
    same site:
        Debt Slayer  -> debtSlayerSave_v1 / debtSlayerCfg_v1
        Grove Keeper -> groveKeeperSave_v1 / groveKeeperCfg_v1
  - "Backup (download)" saves a .json copy (good to drop in
    Google Drive now and then).
  - "Restore" loads a .json backup.
  - "Reset" wipes the tool back to its starting state (cloud keys
    are kept). If you ever pre-load new starting loans in the
    file but already have a saved game, hit Reset once to pick
    up the new defaults.


---------------------------------------------------------------
 USING IT EACH PAYDAY
---------------------------------------------------------------
  1. Pay on your loan servicer's site, choosing the per-loan /
     "specify for each loan" option, sending extra to your
     highest-rate loan first.
  2. In the tracker, enter the amount and hit ATTACK / TEND.
  3. The plan preview mirrors what to send to each loan.
  4. Use "fix balance" / "edit" to match the servicer's exact
     number whenever you want (interest accrual is an estimate).


---------------------------------------------------------------
 CUSTOMIZING
---------------------------------------------------------------
  - Grove Keeper has a built-in loan editor (Add a plot / edit /
    remove) — no code needed.
  - Debt Slayer's loans are defined in the START object near the
    top of its <script> block.
  - Themes (colors) live in the :root CSS variables at the top of
    each file.
