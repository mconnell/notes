## ActiveRecord
Can't be bothered opening up the source to find out what validations are needed on a model instance for it to be valid?
    Model.create.errors.full_messages

## DB Migrations

Setting precision and scale on a decimal:

    change_table :table_name do |t|
      t.decimal :decimal_column_name, :precision => 8, :scale => 2
    end

## Authlogic

    Authlogic::Session::Base.controller = Authlogic::TestCase::MockController.new
