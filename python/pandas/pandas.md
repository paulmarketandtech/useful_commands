### searching for rows with a specific date
df = pd.read_parquet("ohlc_20260716.parquet")
df["date"] = pd.to_datetime(df["date"])

target_date = pd.Timestamp("2026-07-15")
filtered_df = df[df["date"] == target_date]

