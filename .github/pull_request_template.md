## Summary

Describe what changed and why.

## Ownership

- [ ] This changes site-owned configuration, content, data, or an acknowledged local override.
- [ ] Shared theme/runtime changes have been routed to the owning al-folio plugin.

Owning repo (if not starter): <!-- e.g., al-org-dev/al-folio-core -->
Related issue/PR: <!-- link -->

## Validation

- [ ] `npm ci`
- [ ] `npm run lint:prettier`
- [ ] `JEKYLL_ENV=production bundle exec jekyll build`
- [ ] `bundle exec al-folio upgrade audit --no-fail`
- [ ] `bundle exec al-folio upgrade overrides audit`

## Notes

Compatibility, migration implications, and follow-ups:
