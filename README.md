# Laravel Nova Date Inline Field with One Click

This package allow you to edit a Date field in the index page with `one click`

### Installation

        composer require ronnytorres/date-inline

### Usage

#### Add the field to your resource without edition

```php
public function fields(Request $request)
{
        return [

                DateInline::make('Start Date'),

        ];
        
}
```

To edit the Date field you need to click it on.

If you press the `Esc key` or `lost the focues` the field will became not editable.

#### Add the field to your resource and allow to edit with one click

```php
public function fields(Request $request)
{
        return [

                DateInline::make('Start Date')
                        ->inlineOnIndex(),
                
        ];
        
}
```

The `inlineOnIndex` method also accepts a closure with the current request if you want to make it editable dynamically.

```php
public function fields()
{
    return [
        InlineText::make('Start Date')
            ->inlineOnIndex(function (NovaRequest $request) {
                return $request->user()->isAdmin();
            }),
    ];
}
```

#### Show the message 'Date is overdue' at the bottom of the date field

```php
public function fields(Request $request)
{
        return [

        DateInline::make('End Date')
                ->showOverdue(),
        ];
}
```

#### Show a toast message if one date is not greater than other one

```php
public function fields(Request $request)
{
        return [

        DateInline::make('Start Date'),
        
        DateInline::make('End Date')
                ->greaterThan('Start Date),
        ];
}
```

#### The date field in your migrations/database must be nullable

```php
$table->date('data_field_name')->nullable();
```

### Resoure Example
![Image](dateInline_image.PNG)