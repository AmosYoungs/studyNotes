## Antd的Select组件弹出框与Select框分离

<img src="E:\github\studyNotes\assets\img\react\0001.png" style="zoom: 80%;" />

在Select组件中添加属性getPopupContainer={triggerNode => { return triggerNode.parentNode}}即可

```
<Select
                                mode='multiple'
                                style={{ width: '100%' }}
                                key={getSelectDefaultValue(id, 8, rowIndex)}
                                getPopupContainer={triggerNode => {
                                    return triggerNode.parentNode
                                }}
                                placeholder='请选择'
                                disabled={disableEdit}
                                defaultValue={getSelectDefaultValue(id, 8, rowIndex)}
                                onChange={value => {
                                    handleSelectChange(value, `${id}[8][${rowIndex}]`)
                                }}>
                                {colTemplate[6].answerList.map(list => (
                                    <Option value={list.dictValue} key={list.dictValue}>
                                        {list.dictLabel}
                                    </Option>
                                ))}
                            </Select>
```

