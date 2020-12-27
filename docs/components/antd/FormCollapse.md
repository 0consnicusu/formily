```tsx
import React from 'react'
import {
  FormCollapse,
  FormItem,
  Input,
  FormButtonGroup,
  Submit,
} from '@formily/antd'
import { FormProvider, createForm } from '@formily/react'
import { createSchemaField } from '@formily/react-schema-field'
import { Button } from 'antd'
import 'antd/dist/antd.css'

const SchemaField = createSchemaField({
  components: {
    FormItem,
    FormCollapse,
    Input,
  },
})

const form = createForm()

export default () => {
  return (
    <FormProvider form={form}>
      <SchemaField>
        <SchemaField.Void x-component="FormCollapse">
          <SchemaField.Void
            name="panel-1"
            x-component="FormCollapse.CollapsePanel"
            x-component-props={{ key: '1', header: 'A1' }}
          >
            <SchemaField.String
              name="aaa"
              x-decorator="FormItem"
              required
              x-component="Input"
            />
          </SchemaField.Void>
          <SchemaField.Void
            name="panel-2"
            x-component="FormCollapse.CollapsePanel"
            x-component-props={{ key: '2', header: 'A2' }}
          >
            <SchemaField.String
              name="bbb"
              x-decorator="FormItem"
              required
              x-component="Input"
            />
          </SchemaField.Void>
          <SchemaField.Void
            name="panel-3"
            x-component="FormCollapse.CollapsePanel"
            x-component-props={{ key: '3', header: 'A3' }}
          >
            <SchemaField.String
              name="ccc"
              x-decorator="FormItem"
              required
              x-component="Input"
            />
          </SchemaField.Void>
        </SchemaField.Void>
      </SchemaField>
      <Button
        onClick={() => {
          form.query('panel-3').void.get((field) => {
            field.setDisplay(field.display === 'none' ? 'visible' : 'none')
          })
        }}
      >
        显示/隐藏最后一个Tab
      </Button>
      <Submit onSubmit={console.log}>提交</Submit>
    </FormProvider>
  )
}
```