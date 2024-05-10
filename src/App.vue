<script setup>
  import { ref } from 'vue';
  import { Card, Row, Col, Image } from 'ant-design-vue';
  import HelloWorld from './components/HelloWorld.vue'
  import CustomInput from './components/CustomInput.vue';
  import CustomSelect from './components/CustomSelect.vue';
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
  const categories = ref(null);
</script>

<template>
  <HelloWorld />
  <Row>
    <Col :offset="6" :span="12">
      <Card :body-style="{padding: 0}">
          <Row>
            <Col :span="12" class="bg-blue-600 px-0">
              <Row>
                <Col :span="16" :offset="4">
                  <Image 
                    :width="300"
                    :height="300"
                    src="https://aliyuncdn.antdv.com/vue.png"/>
                </Col>
              </Row>
                <h1 class="text-white text-center">Ant design company</h1>
            </Col>
            <Col :span="12">
              <div>
                <CustomInput 
                  label="Name"
                  v-model="age"
                  name="age"
                  id="age"
                  min="0.1"
                  step="0.1"
                  type="number"/>
              </div>
              <div>
                <CustomSelect 
                  label="Categories"
                  v-model="categories"
                  :options="[{value: null, label: 'Elije'}, ...options]"
                  name="categories"/>
              </div>
              {{ categories }}
            </Col>
          </Row>
      </Card>
    </Col>
  </Row>
</template>

