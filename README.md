# repro-crowdin-delete-obsolete

## Steps to reproduce the issue:

1. Create a project in Crowdin
2. Upload sources with: `npx @crowdin/cli upload sources --token ... --project-id 670328 --delete-obsolete --no-auto-update -v --no-progress`

   Output:

   ```
   ✔️  Fetching project info
   ✔️  Directory 'docs'
   ✔️  Directory 'docs/en'
   ✔️  File 'docs/en/test.md'
   ✔️  File 'docs/en/help.md'
   ✔️  No obsolete files were found
   ✔️  No obsolete directories found
   ```

3. Rename `help.md` to `help2.md`
4. Upload sources again with: `npx @crowdin/cli upload sources --token ... --project-id 670328 --delete-obsolete --no-auto-update -v --no-progress`

   Output:

   ```
   ✔️  Fetching project info
   ⏭  File 'docs/en/test.md'
   ✔️  File 'docs/en/help2.md'
   ✔️  No obsolete files were found
   ✔️  No obsolete directories found
   ```

5. Check the Crowdin project and see that `help.md` is still there and not marked as obsolete

## Expected

`help.md` should be marked as obsolete and removed from the Crowdin project.

## Details

Crowdin CLI version: `@crowdin/cli@3.19.2`
