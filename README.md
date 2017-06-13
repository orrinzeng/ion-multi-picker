# Ion-Multi-Picker
本插件修改于 [https://github.com/raychenfj/ion-multi-picker](https://github.com/raychenfj/ion-multi-picker)
具体插件设置请参照原作者。

# 修改内容
在原作者的插件使用中遇到以下问题，当我们设置[(ngModel)]属性的时候，在第一次显示的时候并不会有值。

比如我们设置[(ngModel)] = "default"的，并将default的值设置为default="请选择地址"的时候，请选择地址这个值并不会显示在页面上。

所以我这里对原插件做了一些修改，在原插件的基础上面添加了一个新的属性placeholderText；

### html
```
<ion-item detail-push>
   <ion-label color="dark">所在地区：</ion-label>
     <ion-multi-picker id="default" item-content [(ngModel)]="default" separator="-" [multiPickerColumns]="AddressColumns" placeholderText="{{default}}" cancelText="取消" doneText="确定"></ion-multi-picker>
</ion-item>
```
### ts

```
default = '请选择收货地址';
AddressColumns = [{
    name: 'province',
    options: [
      { text: '四川省', value: '1' }
    ]
  }, {
    name: 'city',
    parentCol: 'province',
    options: [
      { text: '成都市', value: '2', parentVal: '1' }
    ]
  }, {
    name: 'district',
    parentCol: 'city',
    options: [
      { text: '锦江区', value: '3', parentVal: '2' },
      { text: '青羊区', value: '4', parentVal: '2' },
      { text: '金牛区', value: '5', parentVal: '2' },
      { text: '武侯区', value: '6', parentVal: '2' },
      { text: '成华区', value: '7', parentVal: '2' },
      { text: '龙泉驿区', value: '8', parentVal: '2' },
      { text: '青白江区', value: '9', parentVal: '2' },
      { text: '新都区', value: '10', parentVal: '2' },
      { text: '温江区', value: '11', parentVal: '2' },
      { text: '双流区', value: '12', parentVal: '2' },
      { text: '郫都区', value: '13', parentVal: '2' },
      { text: '高新区', value: '14', parentVal: '2' }
    ]
  }];
```
