# Date-Inline Field

## Laravel Nova Date Inline Field

### Installation

        composer require ronnytorres/date-inline

### Usage

#### Add the field to your resource without edition

        public function fields(Request $request)
        {
                return [

                    DateInline::make('Start Date'),

                ];
                
        }


#### Add the field to your resource and allow to edit with one click

        public function fields(Request $request)
        {
                return [

                    DateInline::make('Start Date')
                            ->inlineOnIndex(),
                    
                ];
                
        }

#### Show the message 'Date is overdue' at the bottom of the date field

        public function fields(Request $request)
        {
                return [

                DateInline::make('End Date')
                        ->showOverdue(),
                ];
        }


#### Show a toast message if one date is not greater than other one

        public function fields(Request $request)
        {
                return [

                DateInline::make('Start Date'),
                
                DateInline::make('End Date')
                        ->greaterThan('Start Date),
                ];
        }

#### The date field in your migrations/database must be nullable

        $table->date('data_field_name')->nullable();

### Resoure Example
![Image](dateInline_image.PNG)