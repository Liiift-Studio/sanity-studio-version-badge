# sanity-studio-version-badge

[![npm version](https://img.shields.io/npm/v/@liiift-studio/sanity-studio-version-badge.svg)](https://www.npmjs.com/package/@liiift-studio/sanity-studio-version-badge)

Sanity Studio plugin that shows installed `@liiift-studio` package versions in a fixed bottom-right badge on the structure root page. Surfaces recently published packages and reminds the team when updates are available.

## Install

```bash
npm install @liiift-studio/sanity-studio-version-badge
```

## Usage

Add the plugin to your `sanity.config.ts`:

```typescript
import { defineConfig } from 'sanity'
import { liiiftVersionBadge } from '@liiift-studio/sanity-studio-version-badge'

export default defineConfig({
	projectId: 'your-project-id',
	dataset: 'production',
	plugins: [
		liiiftVersionBadge({
			packages: [
				{ name: '@liiift-studio/sanity-font-manager', version: '2.3.18' },
				{ name: '@liiift-studio/sanity-bulk-data-operations', version: '2.0.0' },
				{ name: '@liiift-studio/sanity-studio-version-badge', version: '2.3.2' },
			],
		}),
	],
})
```

Pass the currently installed version of each `@liiift-studio` package. The badge compares these against the latest npm releases to highlight updates.

## Visibility rules

| Environment | When shown |
|---|---|
| Localhost | Always visible on the structure root |
| Production | On version change, or if more than 7 days since last shown |

- Packages published within the last 7 days are labeled **new**
- npm descriptions are fetched asynchronously and shown in tooltips
- A close button dismisses the badge for 7 days (cookie-based)

## Peer Dependencies

| Package | Version |
|---|---|
| `@sanity/icons` | `>=3` |
| `@sanity/ui` | `>=3` |
| `react` | `>=18` |
| `sanity` | `>=3` |
