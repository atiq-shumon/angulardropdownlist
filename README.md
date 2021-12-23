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
# setting default value
```Javascript
ngAfterViewInit(){
  //console.log(JSON.parse(this.valuejson));
  const toSelect = this.crieteria.find(c => c.value === '3');
    // console.log(toSelect);
     this.searchform.get('crieteria').setValue(toSelect.value);
}
```

#### Dropdown list and service
---------------------------------------
```
_serviceSubscription:Subscription;
------------------------------------------------
constructor( ......., private dropdowneventservice:DropdownEventService){
 this._serviceSubscription=this.dropdowneventservice.dropdownClicked.subscribe({
    next: (name: String) => {
        if(name==='CustomerId'){
         // console.log(name);
          //  var loctotal=this.formComponent.masterForm.controls['nettotal'].value;
          //console.log(this.formComponent.paramForm.controls['param1'].value);
          if(typeof this.formComponent.masterform.get('CustomerId')!=='undefined'){
            // console.log('prod id');
            // console.log(this.formComponent.masterform.get('prodId'));
            //console.log(this.formComponent.masterformFieldConfig);
           // const toSelect = this.formComponent.masterformFieldConfig[2].options.find(c => c.value == this.formComponent.masterform.get('CustomerId').value);
            //  console.log(toSelect);

              this.populateAlternateNames(this.formComponent.masterform.get('CustomerId').value);
          }

           // this.populateoptions(this.formComponent.paramForm.controls['param1'].value,this.formComponent.paramForm.controls['param2'].value);
          }
     }
  });
  
  -------------------
    ngOnDestroy(): void {
    this._serviceSubscription.unsubscribe();
  }
```

