Description: Use this skill for 'email routine triage'.

# Email routine triage skill

## Classification

'TO_DELETE' indicators:
- unsolicited promotions
- suspicious links
- phishing attempts
- requests for sensitive data
- scam language
- irrelevant marketing
- software update newletter
- customer-related topics

'TO_ARCHIVE' indicators:
- business communication
- known contacts
- ongoing conversations
- related to software development or content creation
- non-marketing or no application/service update

'TO_REPLY' indicators:
- personal email
- from know email address

## STEPS

- get all unread inbox with `gog gmail search "is:unread"`
- if no unread messages - notify user
```
<b>📭 Email routine triage</b>

<blockquote>No Unread messages found!</blockquote>
```
- if unread messages:
    - classify messages in you memory as 'TO_DELETE', 'TO_ARCHIVE', 'TO_REPLY'
    - messages marked as 'TO_DELETE' delete with `gog gmail batch delete <messageId> <messageId>`
    - messages marked as 'TO_ARCHIVE' put to archive with `gog gmail batch modify <messageId> <messageId> --remove UNREAD --remove INBOX`
    - messages marked as 'TO_REPLY':
        - read messages one by one with `gog gmail thread get <threadId>`
        - if message contains event with clear date and time, add event to calendar with 
        ```
            gog calendar create primary \
            --summary "{{EVENT_SUMMARY}}" \
            --from 2025-01-15T10:00:00Z \
            --to 2025-01-15T11:00:00Z
        ```
        - draft professional reply with `gog gmail drafts create --reply-to-message-id <messageId> --quote --subject "Re: Hi" --body "My reply"`
        - put to archive with `gog gmail batch modify <messageId> <messageId> --remove UNREAD --remove INBOX`
- Reply user with message:
```
<b>📬 Email routine triage</b>

<blockquote expandable>{{TOTAL_AMOUNT}} of emails processed

- id: {{email_id}}
- from: {{email_from}}
- title: {{email_title_}}
- action: deleted|archived|drafted

...
</blockquote>
```


## INSTRUCTIONS

- Manage Gmail communications using the `gog` CLI.
- Mandatory tool: Use the `shell` tool to execute `gog` commands.
