<script setup>
  import { reactive, ref } from 'vue';
  import { Card, Row, Col, Image } from 'ant-design-vue';
  import HelloWorld from './components/HelloWorld.vue'
  import CustomInput from './components/CustomInput.vue';
  import CustomSelect from './components/CustomSelect.vue';
  import CustomCheckbox from './components/CustomCheckbox.vue';
  import CustomRadioButton from './components/CustomRadioButton.vue';
  const age = ref(1);
  const options = [
    {
      value: 'food',
      label: 'Food',
    },
    {
      value: 'vehicles',
      label: 'Vehicles',
    },
    {
      value: 'kitchen',
      label: 'Kitchen',
    },
  ];

  const formState = reactive({
    name: '',
    category: null,
    clean: false,
    married: 0,
  });
</script>

<template>
  <Row>
    <Col :offset="6" :span="12">
      <Card>
          <Row>
            <Col :span="6">
              <CustomInput 
                label="Name"
                v-model="formState.name"/>
            </Col>
            <Col :span="6">
              <CustomSelect 
                label="Categories"
                :options="options"
                v-model="formState.category"/>
            </Col>
            <Col :span="6">
              <CustomCheckbox 
                label="Clean"
                v-model="formState.clean"/>
            </Col>
            <Col :span="6">
              <CustomRadioButton 
                label="Yes"
                v-model="formState.married"
                name="married"
                :value="1"/>
              <CustomRadioButton 
                label="No"
                v-model="formState.married"
                name="married"
                :value="0"/>
            </Col>
          </Row>
      </Card>
      <p>{{ formState }}</p>
    </Col>
  </Row>
</template>

