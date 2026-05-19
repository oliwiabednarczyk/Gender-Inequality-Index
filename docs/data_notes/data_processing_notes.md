# Data Processing Notes

## Dataset Structure

The collected Eurostat datasets appeared in multiple structural formats:

* Precomputed gap indicators (e.g. gender employment gap)
* Percentage values separated by gender
* Absolute count values separated by gender

To standardize the processing workflow, all datasets were transformed into a unified structure containing:

1. `Country`
2. `Year`
3. One or more of the following value types:

   * `F_Value` → decimal value representing the female observation
   * `M_Value` → decimal value representing the male observation
   * `Gap_Value` → either:

     * directly provided by the source dataset, or
     * calculated using the formula:

```plaintext
Gap_Value = F_Value - M_Value
```

At this stage, the directionality of `Gap_Value` has not yet been standardized. Depending on the metric, higher values may represent either more favorable or less favorable outcomes. Direction alignment and normalization will be handled during the index construction phase.

---

## Timeframe Selection

Some datasets included observations for the year 2025. However, due to incomplete coverage across multiple indicators, only the 2021–2024 period was retained for the final analytical dataset to ensure temporal consistency across all metrics.

---

## Data Quality & Missing Values

Some datasets contained:

* empty observations
* estimated values
* provisional values
* break-in-time-series annotations
* statistically insignificant observations

Due to the lack of a more reliable replacement strategy and to preserve dataset completeness, these values were retained as provided by Eurostat.

---

## Dataset-Specific Transformations

### `ed_persons_with_tertiary_education_in_stem`

The dataset contained both:

* percentage-of-population values
* absolute counts in thousands of persons

Only percentage values were retained, as both formats represented the same underlying information while percentages provided better cross-country comparability.

---

### `students_enrolled_in_tertiary_education`

The original dataset contained absolute counts of students.

To improve comparability with other indicators, female and male participation shares were calculated using the following formulas:

```plaintext
F_Value = F_Count / (F_Count + M_Count) * 100
M_Value = M_Count / (F_Count + M_Count) * 100
```

---

### `seats_held_by_women_in_parliaments_governments`

The final `F_Value` was calculated as the arithmetic average of:

* percentage of women in national governments
* percentage of women in national parliaments

---

### `s_overall_life_satisfaction`

Unlike most indicators, life satisfaction values were reported on a 1–10 scale rather than a percentage-based scale.

No rescaling was applied during the processing phase. Any normalization required for index construction will be handled in a later stage.

---

### `self_reported_unmet_needs_for_medical_examination`

The category `"NO_UNMET"` was excluded from the dataset.

Additionally, only observations corresponding to the `"TOTAL"` degree of urbanization were retained to ensure consistency across countries and reduce unnecessary segmentation.

---

## Country-Year Completeness Validation

Some datasets included observations for countries outside the EU (e.g. Turkey, Albania) or contained incomplete yearly coverage.

To ensure consistency across the analytical dataset, only country-metric combinations containing all four years (2021–2024) were retained.

The following validation procedure was applied:

1. Group data by:

   * `Dimension`
   * `Metric`
   * `Country`

2. Count distinct years for each group

3. Retain only groups where:

```plaintext
YearCount = 4
```

4. Merge the filtered groups back into the original dataset using an inner join on:

   * `Dimension`
   * `Metric`
   * `Country`

This ensured that only countries with complete temporal coverage remained in the final processed dataset.

---

## Additional Notes

A `SourceTable` column was added to all transformed datasets to preserve traceability and improve debugging and validation workflows during later stages of the project.
