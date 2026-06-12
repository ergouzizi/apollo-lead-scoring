# Excel Fields

## Base Fields To Preserve

- Company ID
- Company Name
- Apollo Link
- Website URL
- All Social Links
- Batch No.
- Batch Name
- Industry
- Keywords
- Source File

## Judgement Fields

- 公司简介信息
- 客户类型判断
- 适合产品方向
- 匹配理由
- 开发切入点
- 官网验证状态
- 官网验证摘要
- 不适合原因
- 社媒验证状态
- 社媒活跃度
- 社媒近6个月业务信号
- 社媒匹配判断
- 社媒辅助评分调整
- 社媒验证摘要
- 综合匹配评分
- 综合开发建议

Product-specific level columns may differ:

- 数字标牌匹配层级 / 综合数字标牌匹配层级
- Scanner匹配层级 / 综合Scanner匹配层级
- POS匹配层级 / 综合POS匹配层级

## JSON Keys

The writeback scripts expect these keys:

- `company`
- `customer_type`
- `product_direction`
- `score`
- `level`
- `reason`
- `cut_in`
- `website_status`
- `website_summary`
- `unsuitable_reason`
- `social_status`
- `social_activity`
- `social_signal`
- `social_judgement`
- `social_adjust`
- `development_advice`

## Writing Style

- `匹配理由`: evidence and business logic, not keyword arithmetic.
- `开发切入点`: one actionable salesperson sentence.
- `官网验证摘要`: source types plus key evidence.
- `综合开发建议`: whether to follow up and how.
- `不适合原因`: required for low and unsuitable companies.
