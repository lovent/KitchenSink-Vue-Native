
<template>
  <nb-container :style="{ backgroundColor: '#fff' }">
        <nb-header>
          <nb-left>
            <nb-button
              transparent
              :onPress="() => this.props.navigation.goBack()"
            >
              <nb-icon name="arrow-back" />
            </nb-button>
          </nb-left>
          <nb-body :style="{flex: 3}">
            <nb-title>Custom Title</nb-title>
          </nb-body>
          <nb-right />
        </nb-header>
        <nb-content>
            <nb-form>
                <nb-picker
                    mode="dropdown"
                    iosHeader="Your Header"
                    :iosIcon="getIosIcon()"
                    :style="stylesObj.pickerContainer"
                    :selectedValue="selected1"
                    :onValueChange="onValueChange"
                >
                    <item label="Wallet" value="key0" />
                    <item label="ATM Card" value="key1" />
                    <item label="Debit Card" value="key2" />
                    <item label="Credit Card" value="key3" />
                    <item label="Net Banking" value="key4" />
                </nb-picker>
            </nb-form>
        </nb-content>
      </nb-container>
</template>


<script>
import React from "react";
import { Platform } from "react-native";
import { Picker, Icon } from "native-base";

export default {
  components: { Item: Picker.Item },
  data: function() {
    return {
      selected1: "key1",
      stylesObj: {
        pickerContainer: {
          width: Platform.OS === "ios" ? null : 120
        }
      }
    };
  },
  methods: {
    onValueChange: function(value) {
      this.selected1 = value;
    },
    getIosIcon: function() {
      return <Icon name="ios-arrow-down-outline" />;
    }
  }
};
</script>


<style>
.body-icon-color {
  color: #999;
}
</style>
