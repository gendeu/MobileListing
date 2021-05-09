<template>
  <view class="container">
    <text :style="{color: 'green', fontSize: 20}">My Catalog App!</text>
    <text>{{ myInput }}</text>
    <image
      :style="{width: 50, height: 50}"
      :source="{uri: 'https://facebook.github.io/react-native/docs/assets/favicon.png'}"
    />
    <text-input
      :style="{height: 40, width: 100, borderColor: 'gray', borderWidth: 1}"
      v-model="myInput"
    />
    <touchable-opacity 
      :on-press="handleButton"
      :style="{backgroundColor: 'red', marginTop: 3}"
    >
      <text :style="{color: 'white', padding: 10}">Button</text>
    </touchable-opacity>

    <!-- <flat-list
        :data="countries"
        :render-item="({item}) => renderList(item)"
    /> -->
    <scroll-view :style="{width: '100%'}">
      <view class="border" v-for="(country, index) in countries" :key="index">
        <touchable-opacity class="flex-container" :on-press="() => handleListTap(country)">
          <image
            :style="{width: 40, height: 40, borderRadius: 25, marginRight: 8}"
            :source="{uri: country.imageSrc}"
          />
          <text>{{ country.name }}</text>
        </touchable-opacity>
      </view>
    </scroll-view>
  </view>
</template>

<script>
// import React from 'react';
// import {Text} from 'react-native';

export default {
  props: {
    navigation: {
      type: Object
    }
  },
  data() {
    return {
      myInput: '',
      message: 'Hello Deo',
      countries: [
        { id: 0, name: "Australia", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 1, name: "Belgium", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 2, name: "Bulgaria", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 3, name: "Canada", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 4, name: "Switzerland", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 5, name: "China", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 6, name: "Czech Republic", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 7, name: "Germany", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 8, name: "Spain", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 9, name: "Ethiopia", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 10, name: "Croatia", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 11, name: "Hungary", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 12, name: "Italy", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 13, name: "Jamaica", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 14, name: "Romania", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 15, name: "Russia", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
        { id: 16, name: "United States", imageSrc: "https://www.countryflags.io/ph/flat/64.png" },
      ],
    };
  },
  methods: {
    handleButton() {
      alert(this.myInput),
      this.myInput = '',
      this.navigation.navigate("Home");
    },
    handleListTap(country) {
      console.log(country.name)
    },
    // renderList: (item) => {
    //   return (<Text>{item.name}</Text><img>{item.name}</Text>)
    // }
  }
}
</script>
<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
.border {
  border-bottom-width: 1;
  border-color: gray;
  width: 100%;
  padding: 15
}
.flex-container {
  flex-direction: row;
  align-items: center;
}
</style>
