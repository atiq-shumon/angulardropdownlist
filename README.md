# Angular Material Components
### Dropdown link- select search link
- [angular material select search link](https://www.npmjs.com/package/ngx-mat-select-search)
- [angular material stackbiz example](https://stackblitz.com/edit/mat-select-search)
- [search/dropdown filter example](#filter-example)
```<div  [formGroup]="formGroup" style="width:100%;">
    <mat-form-field style="width:100%;">
        <mat-select  (selectionChange)="onSelectClicked($event.value)" id="companyctl" placeholder="Company"  [formControlName]="controlname" >
          <mat-select-search #companyFilterCtrl></mat-select-search>
           <mat-option *ngFor="let company of companies|filter:companyFilterCtrl.value" [value]="company.value">
          {{company.display}}
         </mat-option>
         </mat-select>
        </mat-form-field>

      </div>Javascript

```

Display a component
Let's display a slider component in your app and verify that everything works.

#### You need to import the MatSliderModule that you want to display by adding the following lines to your app.module.ts file.

```Javascript
 <mat-form-field appearance="fill">
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
</mat-form-field>

```

# filter example
``` Javascript
 serachInSmartCombo(data:string){

              if(data.length>0) {
                this.suppliers=this.suppliersbkp;
                let filtered=this.suppliers.filter(vl=>vl.display.toUpperCase().indexOf(data.toUpperCase())!==-1);
                this.suppliers=filtered;
              }
              else{
                this.suppliers=this.suppliersbkp;
              }

}
```

