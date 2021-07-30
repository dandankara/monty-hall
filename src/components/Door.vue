<template>
  <div class="door-area">

    <!-- Div do porta da porta -->
    <div class="door-frame" :class="{ selected }">
      <Gift v-if="open && hasGift" />
    </div>
    
    <!-- Div da porta em si -->
    <div class="door" :class="{ open }" @click="selected = !selected">

      <!-- Div do número da porta -->
      <div class="number" :class="{ selected }">{{ number }}</div>

      <!-- div da maçaneta -->
      <div class="knob" @click.stop="open = true" :class="{ selected }"></div>
    </div>
  </div>
</template>

<script>
import Gift from "./Gift";
export default {
  name: "Door",
  components: { Gift },
  props: {
    number: {},
    hasGift: { type: Boolean },
  },
  data: function () {
    return {
      open: false,
      selected: false,
    };
  },
};
</script>

<style>
:root {
  --door-border: 5px solid brown;
  --selected-border: 5px solid yellow;
}

/* Area da porta */
.door-area {
  position: relative;
  width: 200px;
  height: 310px;
  border-bottom: 10px solid #aaa;
  margin-bottom: 20px;
  font-size: 2.5rem;

  display: flex;
  justify-content: center;
}

/* Portal da porta */
.door-frame {
  position: absolute;
  height: 300px;
  width: 180px;

  border-left: var(--door-border);
  border-top: var(--door-border);
  border-right: var(--door-border);

  display: flex;
  justify-content: center;
}

/* Porta em si */
.door {
  position: absolute;
  top: 5px;
  height: 295px;
  width: 170px;
  background-color: chocolate;
  align-items: center;
  display: flex;
  flex-direction: column;
  padding: 1.2rem;
}

/* Maçaneta */
.door .knob {
  height: 20px;
  width: 20px;
  border-radius: 50%;
  background-color: brown;

  align-self: flex-start;
  margin-top: 5rem;
}

/* Portal da porta se for selecionado fica amarelo */
.door-frame.selected {
  border-left: var(--selected-border);
  border-top: var(--selected-border);
  border-right: var(--selected-border);
}

/* Se selecionado deixa amarelo */
.door .number.selected {
  color: yellow;
}

/* Deixa a maçaneta amarela */
.door .knob.selected {
  background-color: yellow;
}

.door.open {
  background-color: #0005;
}

.door.open .knob{
  display: none;
}

.door.open .number{
  display: none;
}
</style>