# angular value accessor template

```js
@Component({
  selector: 'app-controller',
  templateUrl: './controller.component.html',
  styleUrl: './controller.component.sass',
  providers: [
    {
      provide: NG_VALUE_ACCESSOR,
      useExisting: forwardRef(() => ControllerName),
      multi: true,
    },
  ],
})
export class ControllerName implements ControlValueAccessor {
  @Input() value: PartnerDto | null = null
  disabled = false

  //call once when init component
  writeValue(value: any) {
    this.value = value
  }

  //call this when change value for trigger formControl/formControlName
  onChange(value: any) {
    this.value = value
  }

  registerOnChange(fn: any) {
    this.onChange = fn
  }

  setDisabledState(isDisabled: boolean) {
    this.disabled = isDisabled
  }

  registerOnTouched() {}
}
```
