---
machine_translated: true
machine_translated_rev: d734a8e46ddd7465886ba4133bff743c55190626
toc_priority: 61
toc_title: "\u8A2D\u5B9A\u30D7\u30ED\u30D5\u30A1\u30A4\u30EB"
---

# 設定プロファイル {#settings-profiles}

設定プロファイルは、同じ名前でグループ化された設定の集合です。 各clickhouseユーザプロファイル.
プロファイル内のすべての設定を適用するには、 `profile` 設定。

例えば:

インストール `web` プロフィール

``` sql
SET profile = 'web'
```

設定プロファイルは、user configファイルで宣言されます。 これは通常 `users.xml`.

例えば:

``` xml
<!-- Settings profiles -->
<profiles>
    <!-- Default settings -->
    <default>
        <!-- The maximum number of threads when running a single query. -->
        <max_threads>8</max_threads>
    </default>

    <!-- Settings for quries from the user interface -->
    <web>
        <max_rows_to_read>1000000000</max_rows_to_read>
        <max_bytes_to_read>100000000000</max_bytes_to_read>

        <max_rows_to_group_by>1000000</max_rows_to_group_by>
        <group_by_overflow_mode>any</group_by_overflow_mode>

        <max_rows_to_sort>1000000</max_rows_to_sort>
        <max_bytes_to_sort>1000000000</max_bytes_to_sort>

        <max_result_rows>100000</max_result_rows>
        <max_result_bytes>100000000</max_result_bytes>
        <result_overflow_mode>break</result_overflow_mode>

        <max_execution_time>600</max_execution_time>
        <min_execution_speed>1000000</min_execution_speed>
        <timeout_before_checking_execution_speed>15</timeout_before_checking_execution_speed>

        <max_columns_to_read>25</max_columns_to_read>
        <max_temporary_columns>100</max_temporary_columns>
        <max_temporary_non_const_columns>50</max_temporary_non_const_columns>

        <max_subquery_depth>2</max_subquery_depth>
        <max_pipeline_depth>25</max_pipeline_depth>
        <max_ast_depth>50</max_ast_depth>
        <max_ast_elements>100</max_ast_elements>

        <readonly>1</readonly>
    </web>
</profiles>
```

この例では、: `default` と `web`. その `default` プロファイルには特別な目的があります。 つまり、 `default` オプションの設定デフォルトを設定します。 その `web` プロファイルは通常のプロファイルです。 `SET` HTTPクエリでURLパラメーターを照会または使用する。

設定プロファイルは相互に継承できます。 継承を使用するには、一つまたは複数を指定します `profile` プロファイルにリストされている他の設定の前に設定します。 ある設定が異なるプロファイルで定義されている場合は、最新の設定が使用されます。

[元の記事](https://clickhouse.tech/docs/en/operations/settings/settings_profiles/) <!--hide-->
