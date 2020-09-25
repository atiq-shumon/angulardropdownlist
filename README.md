# angularframework
Angular Framework description
description here
dropdown list field:

Display a component
Let's display a slider component in your app and verify that everything works.

#### You need to import the MatSliderModule that you want to display by adding the following lines to your app.module.ts file.

```<mat-form-field appearance="fill">
  <mat-label>Toppings</mat-label>
  <mat-select [formControl]="toppings" multiple>
    <mat-select-trigger>
      {{toppings.value ? toppings.value[0] : ''}}
      <span *ngIf="toppings.value?.length > 1" class="example-additional-selection">
        (+{{toppings.value.length - 1}} {{toppings.value?.length === 2 ? 'other' : 'others'}})
      </span>
    </mat-select-trigger>
    <mat-option *ngFor="let topping of toppingList" [value]="topping">{{topping}}</mat-option>
  </mat-select>
</mat-form-field>```
