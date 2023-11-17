### Grid 栅格中a-col高度不一致

![img](image/172b6bbd8fd04adctplv-t2oaga2asx-zoom-in-crop-mark1512000.webp)

解决方案：

使用flex布局的a-row

```vue
<a-row type=flex>
    <a-col>
    </a-col>
</a-row>
```

这样a-row的每一个a-col高度都相同

![image-20230915095214460](image/image-20230915095214460.png)



