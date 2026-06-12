# Apollo Lead Scoring Workflow

## Standard Run

1. Inspect the workbook:
   - Confirm target sheet.
   - Confirm data row count.
   - Confirm scoring/writeback columns.
   - Confirm existing `freeze_panes`.
2. Create a run cache directory:
   - Example: `数字标牌公司数据缓存/agent_judgement_YYYYMMDD_all182`
   - Keep raw page cache, evidence packs, judgement JSON, logs, and summaries together.
3. Export evidence:
   - Homepage from `Website URL`.
   - Search query using company name plus product terms.
   - Up to 3 supplemental pages from the same domain: About, Products, Services, Solutions.
   - Social pages only as auxiliary evidence.
4. Generate Agent judgements:
   - Use product-specific rules.
   - Do not use keyword arithmetic as the final score.
   - Record evidence source types in `官网验证摘要`.
5. Write back in batches:
   - Back up before each write.
   - If workbook is locked, write a timestamped copy.
   - Set `freeze_panes=None`.
6. Validate:
   - Row count, score range, level thresholds, required fields, unsuitable reasons, social adjustment values.
7. Update project `agent.md`:
   - Target workbook and sheet.
   - Cache directory and scripts.
   - AnySearch stats.
   - Final score distribution.
   - High-score list and known feedback overrides.
   - Lessons learned.

## Agent Judgement JSON

Each judgement item should include:

```json
{
  "company": "Company Name exactly as in Excel",
  "customer_type": "软件/CMS平台商",
  "product_direction": "10.1/14/15.6英寸室内数字标牌终端",
  "score": 86,
  "level": "高",
  "reason": "Evidence-based fit reason in Chinese.",
  "cut_in": "Actionable salesperson angle in Chinese.",
  "website_status": "已访问",
  "website_summary": "来源：首页/About/产品页。关键证据...",
  "unsuitable_reason": "",
  "social_status": "部分检索",
  "social_activity": "未知",
  "social_signal": "未发现明确近6个月业务信号",
  "social_judgement": "中性",
  "social_adjust": 0,
  "development_advice": "One actionable sentence."
}
```
