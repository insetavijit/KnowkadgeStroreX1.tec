---
description: Create a curriculum topic file following the LangChain syllabus pattern
---

# Prompt Template for Curriculum Topic Files

Use this prompt to generate curriculum topic files (e.g., LC10.1.1, LC3.2.4) that match the established pattern.

---

## PROMPT

```
Create a curriculum topic file for **[TOPIC_ID] [TOPIC_NAME]** following this exact structure:

### STRUCTURE REQUIREMENTS:

1. **SUBTOPIC TABLE (Lines 1-7)**
   - 4 columns: Subtopic | Focus & Purpose | Key Concepts / Details | One-Line Recall
   - Exactly 5 rows for subtopics numbered [TOPIC_ID].1 through [TOPIC_ID].5
   - Use bold for subtopic names: **[TOPIC_ID].1 Name**
   - Keep One-Line Recall under 70 characters

2. **MAIN HEADING**
   - Format: `# [Topic Name]: [Thematic/Metaphorical Title]`
   - Include an intro paragraph (2-3 sentences) establishing the architectural importance

3. **NUMBERED SECTIONS (5-7 sections)**
   Each section should include:
   - `## N. Section Title`
   - Explanatory prose (2-4 paragraphs)
   - At least ONE of: ASCII diagram, code example, or bullet list
   - Bold key terms on first use

4. **ASCII DIAGRAM (Required in at least one section)**
   Use box-drawing style:
   ```
   ┌─────────────────────────────────┐
   │         Layer Name              │
   ├─────────────────────────────────┤
   │         Next Layer              │
   └─────────────────────────────────┘
   ```

5. **CODE EXAMPLES**
   - Use Python with syntax highlighting
   - Include comments explaining key lines
   - Keep examples minimal but functional

6. **QUICK REFERENCE TABLE (Final section)**
   - 2 columns: Concept | Key Point
   - 6-8 rows summarizing the entire topic
   - Last row should highlight the main benefit

### WRITING STYLE:
- Professional, architectural perspective
- Use metaphors to explain abstract concepts (e.g., "Lego blocks", "Clean Laboratory")
- Target audience: Developers building production LLM applications
- Tone: Confident, instructional, not academic
- Avoid filler words; every sentence should add value

### CONTENT CONTEXT:
[Paste the parent topic table row here to understand scope]
[Paste the syllabus section description for broader context]

### OUTPUT:
Generate the complete markdown file ready to save.
```

---

## EXAMPLE USAGE

To create LC10.1.2:

```
Create a curriculum topic file for **LC10.1.2 Invoke Method** following this exact structure:

[... structure requirements as above ...]

### CONTENT CONTEXT:
Parent row: **[[LC10.1.2 Invoke Method]]** | invoke() semantics; single input processing; return values. Core method.

Syllabus context: LC10 covers LCEL as the modern standard for building LangChain applications. Focus on the Runnable protocol, streaming architecture, and async patterns.
```

---

## CHECKLIST BEFORE SAVING

- [ ] Subtopic table has exactly 5 rows with 4 columns
- [ ] Main heading uses metaphorical/thematic title
- [ ] At least one ASCII diagram present
- [ ] At least 2 code examples with comments
- [ ] Quick Reference table at the end
- [ ] Total length: 100-150 lines
- [ ] No placeholder text remaining
