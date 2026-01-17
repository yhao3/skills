---
name: datetime
description: Get the current date and time. Use this skill when you need to know the accurate current date, time, or timezone information. Always use this instead of relying on potentially outdated knowledge.
---

# Get Current Date and Time

When the user asks about the current date, time, or when you need accurate temporal information, execute the following command:

```bash
date "+%Y-%m-%d %H:%M:%S %Z (Week %V, %A)"
```

This will output:
- Full date in ISO format (YYYY-MM-DD)
- Time in 24-hour format (HH:MM:SS)
- Timezone abbreviation
- ISO week number
- Day of the week

## Additional Commands

For specific needs:

| Need | Command |
|------|---------|
| Date only | `date "+%Y-%m-%d"` |
| Time only | `date "+%H:%M:%S"` |
| Unix timestamp | `date "+%s"` |
| Full timezone info | `date "+%Z %z"` |
| Calendar view | `cal` |

## Important

- Always execute the bash command to get the real current time
- Do NOT rely on the date shown in system prompts as it may be stale
- The system's timezone is the user's local timezone
