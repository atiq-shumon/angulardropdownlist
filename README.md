[Important Links]

[Back to Angular material Framework](https://github.com/atiq-shumon/angularframework)


# Angular Material Components
### Dropdown link- select search link || [Populating dropdownlist data leveraging JSON](#Populating-dropdownlist-data-leveraging-JSON) || [Getting key value of Drop down list](#Getting-Key-value-of-Dropdownlist)

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

## Populating with data
```Javascript
populateproducts(val:any){
  let companyId=val;
  this.products=[];
  this.balancetransferformgroup.get("productid").setValue('');
  let path=this.path+"/"+"sharedpage"+"/getproduct";
  let json={ActionControlMode:'company_wise','Param1':companyId};
  //console.log(json);
 // console.log(path);
  this.progressbar.start();
  this.subscription=this.httpServices.postData(json,path).subscribe(data=>{
   //console.log(data);
    let ddldata=data.map(x=>({'value': x.productID,'display':x.productName}));
    this.products=ddldata;
  },(error:any)=>{this.toasterService.showToaster(error.toString(),'red-snackbar')},
  ()=>{this.progressbar.stop();}

    )
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

#### Dropdown Filter Split push
```
  // const toSelect = this.salesmodes.find(c => c.value === 'C');

    //  this.searchform= new FormGroup({
    //   crieteria: new FormControl('',Validators.required),
    //   searchtext: new FormControl('',[Validators.required,Validators.minLength(2)])
    // });
    // let commentsloc=this.commentsstring.split("╛");
    // //console.log(commentsloc);
    //    commentsloc.forEach(commentstr => {
    //    let com=commentstr.split('↕');
    //  //  console.log(com);
    //    if(com[0]!==''){

    //    this.comments.push({'commentby':com[0],'timestamp':com[1],'contents':com[2],'status':com[3]});
    //    }
    // });
```

### Populating dropdownlist data leveraging JSON
--------------------------------------------------------
C#
```C#
var customer = new
            {
                CustomerId = depositmaster.Customer.CustomerId,
                CustomerName = depositmaster.Customer.CustomerName
            };
   --------------------------         
   fields.Add(new CompositeFormFieldJson("CustomerId", "", JsonConvert.SerializeObject(my_jsondata), "f", new Validation("true"), "ConsumerCustomerFieldComponent", "false"));            
```
```Javascript
ngAfterViewInit(){
 // console.log(this.customerstring.split("~"));
  // for edit mode if values inputted while creating
  let custs= JSON.parse(this.fieldvalue);
 // console.log(custs);
  if(Object.keys(custs).length>0){
     this.customers.push({value: custs.CustomerId,display: custs.CustomerName});
     this.customersbkp=this.customers;
     // const toSelect = this.customers.find(c => c.value === this.custs[0]);
 //console.log( this.customers);
  this.formGroup.get(this.controlname).setValue(this.customers[0].value);
//  this.onSelectClicked(toSelect)
  }
}
```

## Getting Key value of Dropdownlist
-----------------------------------------
```Javascript
let types=this.paymenttypes.find(c => c.value === paymenttypeid);
      //console.log(this.bankmasterdata);
      let banks=(typeof v.bank!=='undefined')?this.bankmasterdata.find(c => c.value === v.bank):{display:'',value:''};
  
  let data={paymenttype: types.display,paymenttypeoid:types.value, amount: amount, reffnumber: reffnumber, date: date, bankname: banks.display,bankoid:banks.value
        , branchname: branch};

```
