# Hijri Gregorian Datepicker

* Angular datepicker based on [ng-bootstrap](https://ng-bootstrap.github.io/#/components/datepicker/overview) that supports **Gregorian** and **Hijri** calendars. 
* Provides the ability to swap between **Gregorian** and **Hijri** calendars.
* Converts the selected date back and forth when changing the calendar type.
* Provides service `DateFormatterService` to help convert date formats in both calendar types.
* Now it supports Angular v16.

## Examples/Demo
Online demo can be found [here](https://eslamelmadny.github.io/HijriGregorianDatepicker/) 

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Features
* Easy to switch between **Gregorian** and **Hijri** calendars.
* Ability to specify the default calendar type either **Gregorian** or **Hijri**.
* Converting dates when changing the type of calendar.
* Ability to specify min and max values for **Gregorian** and **Hijri**.
* Ability to make it required, readonly, or disabled.

## Installation
>npm i ngx-hijri-gregorian-datepicker

## API
>import { NgxHijriGregorianDatepickerModule } from 'ngx-hijri-gregorian-datepicker';

## @Inputs()
 
| Input              | Type            | Required | Description                                         |
|--------------------|-----------------|----------|-----------------------------------------------------|
| selectedDateType   | DateType        | No       | Default calendar type, will be **Hijri** if not specified. |
| selectedDate       | NgbDateStruct   | No       | Date to bind (two-way binding).                     |
| label              | string          | Yes      | Label will be shown beside the input.               |
| readonly           | boolean         | No       | Specify if the user can write in input manually without selecting from datepicker. |
| isRequired         | boolean         | No       | Specify required or not field.                      |
| disabled           | boolean         | No       | Specify disabled or not.                            |
| minHijri           | NgbDateStruct   | No       | Minimum allowed **Hijri** date to select.           |
| maxHijri           | NgbDateStruct   | No       | Maximum allowed **Hijri** date to select.           |
| minGreg            | NgbDateStruct   | No       | Minimum allowed **Gregorian** date to select.       |
| maxGreg            | NgbDateStruct   | No       | Maximum allowed **Gregorian** date to select.       |
| hijriLabel         | string          | No       | Label for Hijri button, will be 'Hijri' by default. |
| GregLabel          | string          | No       | Label for Gregorian button, will be 'Gregorian' by default. |

## @Outputs()

| Output             | Type                     | Description                                        |
|--------------------|--------------------------|----------------------------------------------------|
| selectedDateChange | EventEmitter of NgbDateStruct | Emitted after selecting a date from the picker.     |

## Dependencies

Make sure that `@ng-bootstrap/ng-bootstrap` and `bootstrap` with appropriate versions to Angular 16.

## Usage

1. Install the package `npm i ngx-hijri-gregorian-datepicker`.
2. Import the `NgxHijriGregorianDatepickerModule` in your app module:
    ```typescript
    import { NgxHijriGregorianDatepickerModule } from 'ngx-hijri-gregorian-datepicker';
    ```
3. In template:
    ```html
    <hijri-gregorian-datepicker
        [label]="'Birth Date'"
        [(selectedDate)]="selectedDate"
        [isRequired]="true"
        [GregLabel]="'Gregorian'"
        [hijriLabel]  ="'Hijri'"
        [selectedDateType]="selectedDateType"
        #datePicker>
    </hijri-gregorian-datepicker>
    ```
4. In typescript file:
    ```typescript
    import { NgbDate } from '@ng-bootstrap/ng-bootstrap';
    import { DateType } from 'ngx-hijri-gregorian-datepicker';  

    @Component({...})
    export class AppComponent {
        date: NgbDate;
        selectedDateType = DateType.Hijri;  // or DateType.Gregorian

        constructor() {}
    }
    ```

## Utilities

>DateFormatterService

| Method                        | Parameter           | Return      | Description                                                                             |
|-------------------------------|---------------------|-------------|-----------------------------------------------------------------------------------------|
| ToBindableHijroDate(hijriDate)| hijriDate: string   | NgbDate     | Receive Hijri date from server as a string and convert to `NgbDate` to bind to the component. Default format `(iD/iM/iYY HH:mm:ss tt)` |
| ToBindableHijroDateUsingFormat(hijriDate, format) | hijriDate: string, format: string | NgbDate | Same as previous method with the ability to provide the format of the receiving date. |
| ToHijri(date)                 | NgbDateStruct       | NgbDateStruct | Convert Gregorian date struct to Hijri struct.                                           |
| ToGregorian(date)             | NgbDateStruct       | NgbDateStruct | Convert Hijri date struct to Gregorian struct.                                          |
| ToString(date)                | NgbDateStruct       | string      | Convert date struct to string `dd/mm/yyyy`                                              |

## Credits
This project is based on [ng-bootstrap](https://ng-bootstrap.github.io/#/components/datepicker/overview), [moment](https://momentjs.com/), and [moment Hijri](https://github.com/xsoh/moment-hijri).

## Maintained by
Rayd Alsayf