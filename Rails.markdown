## DB Migrations

Setting precision and scale on a decimal:

    change_table :table_name do |t|
      t.decimal :decimal_column_name, :precision => 8, :scale => 2
    end
