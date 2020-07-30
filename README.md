# date-inline

        Laravel Nova Date Inline Field

### Installation

        composer require ronnytorres/date-line

### Instructions

#### Add the field to your resource

        DateInline::make('Data_Field_Name'),

#### The database field must be nullable

        $table->date('data_field_name')->nullable();