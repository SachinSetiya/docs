---
api_name: average()
excerpt: Calculate the time-weighted average of values in a `TimeWeightSummary`
topics: [hyperfunctions]
keywords: [average, time-weighted, hyperfunctions, toolkit]
api:
  license: community
  type: function
  toolkit: true
hyperfunction:
  family: time-weighted averages
  type: accessor
  aggregates:
    - stats_agg()
# fields below will be deprecated
api_category: hyperfunction
toolkit: true
hyperfunction_family: 'time-weighted averages'
hyperfunction_subfamily: 'time-weighted averages'
hyperfunction_type: accessor
---

# average() <tag type="toolkit">Toolkit</tag>

```SQL
average(
    tws TimeWeightSummary
) RETURNS DOUBLE PRECISION
```

A function to compute a time-weighted average from a `TimeWeightSummary`.

*   For more information about time-weighted average functions, see the
    [hyperfunctions documentation][hyperfunctions-time-weight-average].
*   For more information about statistical aggregate functions, see the
    [hyperfunctions documentation][hyperfunctions-stats-agg].

### Required arguments

|Name|Type|Description|
|-|-|-|
|`tws`|`TimeWeightSummary`|The input TimeWeightSummary from a [`time_weight`][time_weight] call|

### Returns

|Column|Type|Description|
|-|-|-|
|`average`|`DOUBLE PRECISION`|The time-weighted average computed from the `TimeWeightSummary`|

### Sample usage

```SQL
SELECT
    id,
    average(tws)
FROM (
    SELECT
        id,
        time_weight('LOCF', ts, val) AS tws
    FROM foo
    GROUP BY id
) t
```

[hyperfunctions-time-weight-average]: /timescaledb/:currentVersion:/how-to-guides/hyperfunctions/time-weighted-averages/
[hyperfunctions-stats-agg]: /timescaledb/:currentVersion:/how-to-guides/hyperfunctions/stats-aggs/
[time_weight]: /api/:currentVersion:/hyperfunctions/time-weighted-averages/time_weight/
