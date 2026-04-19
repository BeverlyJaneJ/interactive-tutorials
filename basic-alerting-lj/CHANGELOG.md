# basic-alerting-lj changelog

## 2026-04-17

### Scope and terminology fixes

- Replaced "alert rule form" with "alert GUI" across all guides to match website slide terminology.
- Removed Default/Advanced mode toggle step from `select-data-source` — the learner should leave it on Default without being told about Advanced.
- Removed duplicate naming step from `save-alert-rule` — naming is handled in `navigate-and-name`.

### New guides

- **`navigate-and-name`**: Interactive guide for step 6 (navigate to Alerting > Alert rules > New alert rule, enter rule name). Previously this step had no guide — navigation was incorrectly embedded in `select-data-source`.
- **`create-contact-point-prereq`**: Standalone guide that runs on `/alerting/notifications` with full interactivity (navigate, add contact point, name, email integration, save). Placed as a prereq in the intro module so the learner has a contact point ready before building the alert rule.

### Interactive selectors added

| Guide | Element | Action | Selector |
|-------|---------|--------|----------|
| `navigate-and-name` | Alerting nav item | highlight | `a[data-testid='data-testid Nav menu item'][href='/alerting']` |
| `navigate-and-name` | Alert rules nav item | highlight | `a[data-testid='data-testid Nav menu item'][href='/alerting/list']` |
| `navigate-and-name` | New alert rule button | highlight | `a[href='/alerting/new/alerting']` |
| `navigate-and-name` | Rule name input | formfill | `input[id='name']` |
| `select-data-source` | Data source dropdown | highlight | `input[data-testid='data-testid Select a data source']` |
| `select-data-source` | Explain toggle | highlight | `input[id^='switch-Explain']` |
| `select-metric` | Metric dropdown | highlight | `input[data-testid='data-testid metric select']` |
| `run-query` | Instant radio button | highlight | `input[id^='option-instant-']` |
| `run-query` | Run queries button | button | `Run queries` |
| `notification-message` | Summary field | formfill | `textarea[placeholder='Enter a summary...']` |
| `notification-message` | Description field | formfill | `textarea[placeholder='Enter a description...']` |
| `notification-message` | Runbook URL field | formfill | `input[placeholder='https://']` |
| `create-contact-point` | Contact point picker | highlight | `div[data-testid='contact-point-picker']` |
| `create-contact-point-prereq` | Add contact point button | highlight | `a[aria-label='add contact point']` |
| `create-contact-point-prereq` | Name input | formfill | `input[id='name']` |
| `create-contact-point-prereq` | Integration type | formfill | `input[id='contact-point-type-items.0.']` |
| `create-contact-point-prereq` | Email addresses | formfill | `textarea[id='items.0.settings.addresses']` |
| `create-contact-point-prereq` | Save button | highlight | `button[type='submit']` |

### Contact point restructure

- Split the original `create-contact-point` guide into two:
  - **`create-contact-point-prereq`** — full creation flow, runs before the alert rule (intro module, weight 52)
  - **`create-contact-point`** — select-only flow, runs during alert rule config (section 5 dropdown)
- This avoids the new-tab problem where "View or create contact points" opens `/alerting/notifications` in a separate tab that Pathfinder cannot follow.

### Website slide changes

- **New**: `01-intro/06-create-contact-point/index.md` — prereq slide with `pathfinder_data: basic-alerting-lj/create-contact-point-prereq`
- **Updated**: `02-create-alert-rule/22c-navigate-and-name/index.md` — added `pathfinder_data: basic-alerting-lj/navigate-and-name`, replaced static markdown with `{{< pathfinder/json >}}`
- **Updated**: `04-finish-and-save/30f-create-contact-point/index.md` — title changed to "Select a contact point", script updated for select-only flow
