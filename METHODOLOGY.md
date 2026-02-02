# Tournament Methodology

## Experimental Design

### Objective
Compare 8 LLM providers for security thought leadership content generation using standardized ML evaluation techniques.

### Providers Tested

| Provider | Model | Type | Pricing |
|----------|-------|------|---------|
| DeepSeek | deepseek-chat | API | $0.14/1M input |
| Anthropic | claude-sonnet-4 | API | $3.00/1M input |
| OpenAI | gpt-4o-mini | API | $0.15/1M input |
| Vertex | gemini-2.0-flash | API | $0.075/1M input |
| Azure | gpt-4o-mini | API | $0.15/1M input |
| Groq | llama-3.3-70b | API | $0.05/1M input |
| Ollama | llama3.1:8b | Local | Free |
| Qwen | qwen2.5:32b | Local | Free |

### Controlled Variables

| Variable | Value | Rationale |
|----------|-------|-----------|
| System Prompt | Fixed 4-sentence persona | Consistent role framing |
| User Prompt | Fixed task description | Same requirements |
| Knowledge Base | 5 trends + 5 predictions | Identical grounding |
| Evaluator | DR Zero (BLIND) | No provider knowledge |
| Topic | NHI in cloud-native | Single domain focus |

### Standardized Parameters (Days 1-2)

```yaml
temperature: 0.7
top_p: 0.9
max_tokens: 1024
frequency_penalty: 0.3
presence_penalty: 0.3
```

---

## ML Phases

### Day 1: Zero-Shot Baseline
- No feedback provided
- Pure model capability assessment
- Establishes baseline for comparison

### Day 2: In-Context Learning (ICL)
- Previous day's feedback injected into prompt
- Tests model's ability to incorporate guidance
- Measures learning rate

### Day 3: Parameter Tuning
- Adjusted temperature, penalties based on Day 2 results
- Tests sensitivity to inference parameters
- Identifies optimal settings per model

### Day 4: Competitive Awareness (Few-Shot)
- Winner's response shown as exemplar
- Tests ability to learn from high-quality examples
- "This is what 88/100 looks like"

### Day 5: Full Context
- All previous feedback + competition results
- Maximum information injection
- Tests for overfitting

### Day 6: Per-Model Optimization (Bonus)
- Custom parameters per model
- Model-specific prompt additions
- Demonstrates production tuning potential

---

## Evaluation Criteria

### DR Zero Scoring Dimensions

| Dimension | Weight | Description |
|-----------|--------|-------------|
| Technical Depth | 20 pts | CVEs, attack chains, specific tools |
| Practical Impact | 20 pts | Actionable CISO advice |
| Credibility | 20 pts | Authoritative voice, experience |
| Novelty | 20 pts | Fresh insights, not recycled |
| Presentation | 20 pts | Hook, structure, engagement |

### Verdict Thresholds

- **PUBLISH (80-100)**: Production-ready content
- **REVISE (60-79)**: Needs specific improvements  
- **KILL (0-59)**: Not salvageable

### AI Slop Detection (Automatic Penalties)

- Generic openings: "In today's digital landscape..."
- Buzzword soup: "AI-powered", "next-gen", "holistic"
- Vague advice: "prioritize security", "stay vigilant"
- Corporate speak: "leverage", "synergy", "stakeholders"
- Format crimes: >3 hashtags, >2 emojis

---

## Blind Evaluation Protocol

DR Zero received:
- The generated content only
- No provider name
- No day number
- No previous scores
- No context about the tournament

This ensures unbiased evaluation across all providers and iterations.

---

## Reproducibility

### Running the Tournament

```bash
# Run single day
npx tsx scripts/run-daily-test.ts --day 1

# Run all days
for day in 1 2 3 4 5; do
  npx tsx scripts/run-daily-test.ts --day $day
done

# Run bonus optimization
npx tsx scripts/run-daily-test.ts --day 6
```

### Data Storage

Each day produces:
- `results.json` - Scores, latency, tokens, cost
- `{provider}.md` - Full response + DR Zero assessment
- `SUMMARY.md` - Day analysis

---

## Known Limitations

| Limitation | Impact | Mitigation |
|------------|--------|------------|
| Single evaluator | Potential bias | Future: Multi-evaluator ensemble |
| Small sample | No p-values | Future: 30+ iterations |
| Same topic | May favor some models | Future: Topic rotation |
| Infrastructure variance | Latency differences | Future: Unified gateway |
| Evaluator conflict | Azure evaluates Azure | Future: Independent evaluator |

See FINAL-REPORT.md "What's Next" section for proposed follow-up studies.
