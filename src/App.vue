<script setup>
  import { computed, reactive, ref, watch, nextTick } from 'vue';
  import { Card, Row, Col, Image } from 'ant-design-vue';
  import HelloWorld from './components/HelloWorld.vue'
  import CustomInput from './components/CustomInput.vue';
  import CustomSelect from './components/CustomSelect.vue';
  import CustomCheckbox from './components/CustomCheckbox.vue';
  import CustomRadioButton from './components/CustomRadioButton.vue';
  import { range } from './helpers/range';
  const age = ref(1);
  const tabsRange = computed(() => range(1, numeroMuestras.value, 1));
  const activeKey = ref(0);
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
  const numeroMuestras = ref(1); 
  const formState = reactive([{
    name: '',
    category: null,
    clean: false,
    married: 0,
  }]);
  watch(numeroMuestras, () => {
    activeKey.value = 0
    for (let i = 0; i < formState.length; i++) {
      formState.pop();
    }
    for (let i = 0; i < numeroMuestras.value; i++) {
      formState.push({
        name: '',
        category: null,
        clean: false,
        married: 0,
        children: null,
      });
    }
  });
</script>

<template>
  <Row>
    <Col :offset="6" :span="12">
      <Card>
          <Row>
            <Col :span="6">
              <CustomInput 
                type="number"
                label="Numero de muestras"
                v-model="numeroMuestras"/>
            </Col>
          </Row>
      </Card>
      <p>{{ formState }}</p>
    </Col>
  </Row>
  <Row>
    <Col :offset="3" :span="18">
      <form @submit.prevent="handleSubmit">
        <a-tabs v-model:activeKey="activeKey">
          <a-tab-pane :key="i" :tab="`Tab ${i}`" v-for="i in tabsRange">
            <Row v-if="formState[i - 1]">
              <Col :span="4">
                <CustomInput 
                  label="Name"
                  :required="true"
                  v-model="formState[i - 1].name"/>
              </Col>
              <Col :span="6">
                <CustomSelect 
                  label="Categories"
                  :required="true"
                  :options="options"
                  v-model="formState[i - 1].category"/>
              </Col>
              <Col :span="3">
                <CustomCheckbox 
                  label="Clean"
                  v-model="formState[i - 1].clean"/>
              </Col>
              <Col :span="3">
                <CustomRadioButton 
                  label="Yes"
                  v-model="formState[i - 1].married"
                  name="married"
                  :value="1"/>
                <CustomRadioButton 
                  label="No"
                  v-model="formState[i - 1].married"
                  name="married"
                  :value="0"/>
              </Col>
              <Col :span="5" v-if="formState[i - 1].married">
                <CustomInput 
                  label="Children"
                  type="number"
                  min="0"/>
              </Col>
            </Row>
          </a-tab-pane>
        </a-tabs>
        <button class="py-2 px-3 rounded border-0 bg-green-600 text-white mt-2">Enviar</button>
    </form>
    </Col>
  </Row>
</template>

