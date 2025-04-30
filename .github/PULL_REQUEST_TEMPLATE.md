### dbt Test Checklist for Pull Requests

Use this checklist when submitting or reviewing any PR that includes dbt test files or model changes.

---

#### Test Coverage & Validation
- [ ] Includes at least one test for every new model or metric
- [ ] Covers edge cases (e.g., nulls, zero values, unexpected joins)
- [ ] Drift test included for critical metrics (e.g., ENDING_ARR, row count)
- [ ] Manual `dbt run` completed for test files:
  ```bash
  dbt run --select path:models/tests/<test_file_name>.sql
  ```

---

####  Test File Standards
- [ ] Test file has the standard header block
- [ ] Author, date, purpose, thresholds are filled in
- [ ] Notification simulation included using `log()` block
- [ ] Test file returns rows only if a failure condition is met

---

#### YAML Registration
- [ ] Test is registered in `schema.yml` or `temp_schema.yml`
- [ ] Uses `dbt_utils.expression_is_true` or a custom data test pattern

---

#### Communication
- [ ] Stakeholders notified if the change affects production models
- [ ] Changelog or release notes updated if applicable
