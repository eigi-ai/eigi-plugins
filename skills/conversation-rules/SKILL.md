---
name: conversation-rules
description: "Prompt-writing guardrails for Eigi or Claude agent prompts. Use when creating, revising, or auditing conversation prompts, system prompts, developer instructions, or agent behavior rules, especially for voice/TTS and multilingual Hindi, English, or Hinglish agents. Ensure generated prompts prevent spoken Markdown and punctuation artifacts, require Hindi in Devanagari, keep English in English/Latin script, and produce natural modern Hinglish with Devanagari Hindi words plus English words in Latin script."
---

# Conversation Rules Skill

Use this skill when writing or updating an agent prompt. Add or adapt these rules inside the generated prompt, usually under "Conversation Style", "Language", or "Output Formatting".

## Core Rules

Include these requirements in the agent prompt:

1. Make output speech-safe by default.
2. Match the user's language mix and conversation context.
3. Write Hindi words in Devanagari.
4. Write English words in English/Latin script.
5. Write Hinglish as natural modern Hindi in Devanagari with English words preserved in Latin script.
6. Preserve task-specific conversation rules, persona, and required flow.

## Speech-Safe Output

Require the agent to generate plain conversational text by default, especially for voice or TTS channels.

Avoid user-facing Markdown or formatting syntax that can be spoken aloud incorrectly:

- Bullet dots or Markdown list markers
- Numbered-list markers unless a text-only channel needs them
- Heading hashes
- Backticks
- Bold or italic markers
- Table pipes
- Decorative separators
- Unnecessary quotation marks
- Isolated punctuation symbols

Use normal sentence punctuation only where it helps readability. Do not place punctuation as standalone tokens. Do not write punctuation names such as "dot", "quote", "comma", or "slash" unless the user is asking about the symbol itself.

For voice/TTS responses, prefer short natural sentences over formatting-heavy lists. For text-only channels, allow light structure only when it improves clarity and will not be spoken aloud.

## Hindi, English, and Hinglish

Require the agent to detect the user's language mix and respond in the same style unless the user asks for a different language.

Use these script rules:

- Write Hindi words only in Devanagari.
- Do not romanize Hindi words such as "aap", "nahi", "kya", "karna", "ho gaya", or "theek hai".
- Write English words, product names, brand names, technical terms, IDs, URLs, emails, phone numbers, commands, code, model names, and exact user-provided literals in English/Latin script.
- Do not transliterate English words into Devanagari when the word is being used as English in the conversation.
- For Hinglish, convert the Hindi parts to natural modern Hindi in Devanagari and keep the English parts in Latin script.
- Prefer modern, conversational Hindi over overly Sanskritized or formal Hindi.

Examples:

| Avoid | Prefer |
| --- | --- |
| Aapka payment fail ho raha hai. | आपका payment fail हो रहा है. |
| Kya aap order ID share kar sakte hain? | क्या आप order ID share कर सकते हैं? |
| Nahi, refund kal tak aa jayega. | नहीं, refund कल तक आ जाएगा. |
| Main issue check kar raha hoon. | मैं issue check कर रहा हूँ. |
| OTP ko type karo. | OTP type करें. |

Preserve exact literals when accuracy matters:

- Phone numbers
- Order IDs
- Ticket IDs
- URLs
- Emails
- Usernames
- Product names
- API fields
- Code, commands, and logs
- Quoted user text

## Conversation Behavior

Keep these rules compatible with the rest of the prompt:

- Follow the agent's persona and business process.
- Use conversation history to avoid repeating questions.
- Ask only the follow-up questions needed to complete the task.
- Keep answers concise for voice/TTS.
- Do not mention internal formatting or script-conversion rules to the end user.
- Do not change exact technical content, identifiers, or user-provided evidence while applying language rules.
- If the user requests code, structured data, legal text, or another exact format, prioritize the requested format and preserve required syntax.

## Reusable Prompt Block

Use or adapt this block when generating an agent prompt:

```text
Language and speech-safety rules:
- Respond in clean, speech-friendly plain text unless the channel explicitly requires formatted text.
- Do not use Markdown, bullet markers, headings, table syntax, backticks, decorative punctuation, isolated punctuation symbols, or unnecessary quotes in user-facing replies.
- Do not write punctuation names like "dot", "quote", "comma", or "slash" unless the user is asking about the symbol itself.
- Use Hindi words only in Devanagari script.
- Use English words only in English/Latin script.
- For Hinglish, write natural modern Hindi in Devanagari and keep English words, product names, technical terms, IDs, URLs, phone numbers, emails, and codes exactly in English/Latin script.
- Do not romanize Hindi words such as "aap", "nahi", "kya", "karna", or "ho gaya"; write them as "आप", "नहीं", "क्या", "करना", "हो गया".
- Preserve user-provided identifiers, names, brands, commands, URLs, code, logs, and quoted text exactly.
- Match the user's language mix and tone while following the conversation flow, persona, and task-specific rules.
- Ask only necessary follow-up questions and keep replies concise for voice/TTS.
```

## Validation Checklist

Before finalizing an agent prompt, check that it:

- Includes speech-safe output rules if the agent may speak through TTS.
- Prevents Markdown and standalone punctuation from appearing in spoken replies.
- Explains Hindi, English, and Hinglish script behavior explicitly.
- Preserves exact identifiers and technical strings.
- Does not duplicate the same language rules in multiple conflicting sections.
- Keeps the agent's original task, persona, escalation rules, and business flow intact.