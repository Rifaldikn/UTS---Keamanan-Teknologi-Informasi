<template>
  <v-app>
    <v-container fluid>
      <v-container>
        <v-layout justify-center>
          <h1>UTS Keamanan Teknologi Informasi</h1>
         <h3>RIFALDI KUSNAWAN - 11160910000081</h3>
        </v-layout>
      </v-container>
      <v-layout row wrap justify-center>
        <!--
          <v-flex xs3>
            <v-card class="d-inline-block elevation-6" width="200">
              <v-navigation-drawer floating permanent stateless value="true">
                <v-list dense>
                  <v-list-tile v-for="item in items" :key="item.title" @click="">
                    <v-list-tile-content>
                      <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
                </v-list>
              </v-navigation-drawer>
            </v-card>
          </v-flex>
        -->
        <v-flex xs10 ma-3>
          <v-card class="elevation-6">
            <v-container>
              <p class="title">Substitution Cipher</p>
              <v-form>
                <v-container fluid>
                  <v-layout>
                    <v-flex>
                      <v-layout>
                        <v-textarea
                          outline
                          v-model="input.substitution.str"
                          name="chipher substitution"
                          label="Type text to be encrypt/decrypt by substitution cipher"
                        ></v-textarea>
                      </v-layout>
                      <v-layout row align-center>
                        <v-flex sm6>
                          <v-subheader>
                            Julius Caesar Cipher - shifting</v-subheader
                          >
                        </v-flex>
                        <v-flex sm3>
                          <v-select
                            :items="key.substitution"
                            :menu-props="{ maxHeight: '300'}"
                            label="Characters"
                            v-model="input.substitution.key"
                          ></v-select>
                        </v-flex>
                      </v-layout>
                      <v-btn
                        color="success"
                        @click="subEncrypt(input.substitution.str, input.substitution.key, 1)"
                      >
                        Encrypt
                      </v-btn>
                      <v-btn
                        dark
                        color="indigo"
                        @click="subEncrypt(input.substitution.str, input.substitution.key, 0)"
                      >
                        Decrypt
                      </v-btn>
                    </v-flex>
                    <v-flex xs4>
                      <v-card>
                        <v-subheader>Result :</v-subheader>
                        <!-- <v-container> -->
                        <!-- <v-layout>{{result}}</v-layout> -->
                        <v-textarea
                          v-model="result.substitution"
                          disabled
                          no-resize
                          flat
                          solo
                          class="elevation-0"
                        ></v-textarea>
                        <!-- </v-container> -->
                      </v-card>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-form>
            </v-container>
          </v-card>
        </v-flex>
        <v-flex xs10 ma-3>
          <v-card class="elevation-6">
            <v-container>
              <p class="title">XOR Cipher</p>
              <v-form>
                <v-container fluid>
                  <v-layout>
                    <v-flex>
                      <v-layout>
                        <v-textarea
                          outline
                          v-model="input.xor.str"
                          name="chipher substitution"
                          label="Type text to be encrypt/decrypt by XOR cipher"
                        ></v-textarea>
                      </v-layout>
                      <v-layout row align-center>
                        <!-- <v-flex sm6>
                          <v-text-field
                            label="Key Number"
                            v-model="input.xor.key"
                            outline
                          ></v-text-field>
                        </v-flex> -->
                        <v-flex sm6>
                          <v-select
                            :items="key.substitution"
                            :menu-props="{ maxHeight: '300'}"
                            label="Key"
                            v-model="input.xor.key"
                          ></v-select>
                        </v-flex>
                      </v-layout>
                      <v-btn
                        color="success"
                        @click="xorEncrypt(input.xor.str, input.xor.key)"
                      >
                        Encrypt
                      </v-btn>
                      <!--
                        <v-btn dark color="indigo" @click="subEncrypt(input.xor.str, input.xor.key, 0)"> Decrypt </v-btn>
                      -->
                    </v-flex>
                    <v-flex xs4>
                      <v-card>
                        <v-subheader>Result :</v-subheader>
                        <!-- <v-container> -->
                        <!-- <v-layout>{{result}}</v-layout> -->
                        <v-textarea
                          v-model="result.xor"
                          disabled
                          no-resize
                          flat
                          solo
                          class="elevation-0"
                        ></v-textarea>
                        <!-- </v-container> -->
                      </v-card>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-form>
            </v-container>
          </v-card>
        </v-flex>
        <v-flex xs10 ma-3>
          <v-card class="elevation-6">
            <v-container>
              <p class="title">Transposition Cipher</p>
              <v-form>
                <v-container fluid>
                  <v-layout>
                    <v-flex>
                      <v-layout>
                        <v-textarea
                          outline
                          v-model="input.transpose.str"
                          name="chipher substitution"
                          label="Type text to be encrypt/decrypt by XOR cipher"
                        ></v-textarea>
                      </v-layout>
                      <v-layout row align-center>
                        <v-flex sm6>
                          <v-select
                            :items="key.substitution"
                            :menu-props="{ maxHeight: '300'}"
                            label="Characters"
                            v-model="input.transpose.key"
                          ></v-select>
                        </v-flex>
                      </v-layout>
                      <v-btn
                        color="success"
                        @click="transposeEncrypt(input.transpose.str, input.transpose.key, 0)"
                      >
                        Encrypt
                      </v-btn>
                      <v-btn
                        dark
                        color="indigo"
                        @click="transposeEncrypt(input.transpose.str, input.transpose.key, 1)"
                      >
                        Decrypt
                      </v-btn>
                    </v-flex>
                    <v-flex xs4>
                      <v-card>
                        <v-subheader>Result :</v-subheader>
                        <!-- <v-container> -->
                        <!-- <v-layout>{{result}}</v-layout> -->
                        <v-textarea
                          v-model="result.transpose"
                          disabled
                          no-resize
                          flat
                          solo
                          class="elevation-0"
                        ></v-textarea>
                        <!-- </v-container> -->
                      </v-card>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-form>
            </v-container>
          </v-card>
        </v-flex>
        <v-flex xs10 ma-3>
          <v-card class="elevation-6">
            <v-container>
              <p class="title">Soal1.php Encryption</p>
              <v-form>
                <v-container fluid>
                  <v-layout>
                    <v-flex>
                      <v-layout>
                        <v-textarea
                          outline
                          v-model="input.soal1.str"
                          name="chipher substitution"
                          label="Type NIM to be encrypt/decrypt"
                        ></v-textarea>
                      </v-layout>
                      <v-layout row align-center>
                        <v-flex sm6>
                          <v-select
                            :items="key.substitution"
                            :menu-props="{ maxHeight: '300'}"
                            label="Key"
                            v-model="input.soal1.key"
                          ></v-select>
                        </v-flex>
                      </v-layout>
                      <v-btn
                        color="success"
                        @click="soal1(input.soal1.str, input.soal1.key, 0)"
                      >
                        Encrypt
                      </v-btn>

                      <v-btn
                        dark
                        color="indigo"
                        @click="soal1(input.soal1.str, input.soal1.key, 1)"
                      >
                        Decrypt
                      </v-btn>
                    </v-flex>
                    <v-flex xs4>
                      <v-card>
                        <v-subheader>Result :</v-subheader>
                        <!-- <v-container> -->
                        <!-- <v-layout>{{result}}</v-layout> -->
                        <v-textarea
                          v-model="result.soal1"
                          disabled
                          no-resize
                          flat
                          solo
                          class="elevation-0"
                        ></v-textarea>
                        <!-- </v-container> -->
                      </v-card>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-form>
            </v-container>
          </v-card>
          <v-icon></v-icon>
        </v-flex>
         <v-flex xs10 ma-3>
          <v-card class="elevation-6">
            <v-container>
              <p class="title">Soal2 XOR</p>
              <v-form>
                <v-container fluid>
                  <v-layout>
                    <v-flex>
                      <v-layout>
                        <v-textarea
                          outline
                          v-model="input.soal2.str"
                          name="chipher substitution"
                          label="Type text to be encrypt/decrypt by XOR cipher"
                        ></v-textarea>
                      </v-layout>
                      <v-btn
                        color="success"
                        @click="soal2(input.soal2.str, 0)"
                      >
                        Encrypt
                      </v-btn>
                      
                        <v-btn dark color="indigo" @click="soal2(input.soal2.str, 1)"> Decrypt </v-btn>
                     
                    </v-flex>
                    <v-flex xs4>
                      <v-card>
                        <v-subheader>Result :</v-subheader>
                        <v-textarea
                          v-model="result.soal2"
                          disabled
                          no-resize
                          flat
                          solo
                          class="elevation-0"
                        ></v-textarea>
                         <v-subheader>Key :</v-subheader>
                        <v-textarea
                          height="10"
                          row-height="10"
                          v-model="input.key"
                          disabled
                          no-resize
                          flat
                          solo
                          class="elevation-0"
                        ></v-textarea>
                      </v-card>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-form>
            </v-container>
          </v-card>
        </v-flex>
        <v-flex xs10 ma-3>
          <v-card class="elevation-6">
            <v-container>
              <p class="title">Contoh5 Encryption</p>
              <v-form>
                <v-container fluid>
                  <v-layout>
                    <v-flex>
                      <v-layout>
                        <v-textarea
                          outline
                          v-model="input.contoh5.str"
                          name="chipher substitution"
                          label="Type NIM to be encrypt/decrypt"
                        ></v-textarea>
                      </v-layout>
                      <!--
                        <v-layout row align-center>
                          <v-flex sm6>
                            <v-select
                              :items="key.substitution"
                              :menu-props="{ maxHeight: '300'}"
                              label="Key"
                              v-model="input.contoh.key"
                            ></v-select>
                          </v-flex>
                        </v-layout>
                      -->
                      <v-btn
                        color="success"
                        @click="contoh5(input.contoh5.str)"
                      >
                        Encrypt
                      </v-btn>

                      <!--
                        <v-btn
                          dark
                          color="indigo"
                          @click="soal1(input.soal1.str, input.soal1.key, 1)"
                        >
                          Decrypt
                        </v-btn>
                      -->
                    </v-flex>
                    <v-flex xs4>
                      <v-card>
                        <v-subheader>Result :</v-subheader>
                        <!-- <v-container> -->
                        <!-- <v-layout>{{result}}</v-layout> -->
                        <v-textarea
                          v-model="result.contoh5"
                          disabled
                          no-resize
                          flat
                          solo
                          class="elevation-0"
                        ></v-textarea>
                        <!-- </v-container> -->
                      </v-card>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-form>
            </v-container>
          </v-card>
          <v-icon></v-icon>
        </v-flex>
      </v-layout>
    </v-container>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      result: {
        substitution: "",
        xor: "",
        transpose: "",
        soal1: "",
        soal2: "",
        contoh5: ""
      },
      right: null,
      key: {
        substitution: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
      },
      input: {
        substitution: {
          str: "",
          key: 0
        },
        xor: {
          str: "",
          key: 0
        },
        transpose: {
          str: "",
          key: 0
        },
        soal1: {
          str: "",
          key: 0
        },
        contoh5: {
          str: ""
        },
        soal2: {
          str: "",
          key: 0
        }
      }
    };
  },
  methods: {
    subEncrypt(str, key, mode) {
      if (key < 0) return subEncrypt(str, key + 256);
      var temp = "";
      for (var i = 0; i < str.length; i++) {
        var code = str.charCodeAt(i);
        if (mode) {
          temp += String.fromCharCode((code + key) % 256);
        } else {
          temp += String.fromCharCode((code - key) % 256);
        }
      }
      console.log(temp);
      console.log(this.result);
      this.result.substitution = temp;
    },
    xorEncrypt(str, key) {
      var temp = "";
      console.log(key);
      for (let i = 0; i < str.length; i++) {
        // for (let j = 0; j < key.length; j++)
        temp += String.fromCharCode(str.charCodeAt(i) ^ key % 256);
        console.log(String.fromCharCode(str.charCodeAt(i)));
        // );
      }
      return (this.result.xor = temp);
    },
    transposeEncrypt(str, key, mode) {
      var temp = "";
      var text = str.replace(/\s/g, " ").split("");
      console.log(text);
      for (let i = 0; i < key - mode; i++) {
        for (let j = 0; j < str.length; j += key - mode) {
          var h = i + j;
          console.log(i, j, h);
          if (text[h] != " " && text[h] != undefined) {
            temp += text[h];
          }
          console.log(text[h]);
        }
      }
      return (this.result.transpose = temp);
    },
    soal1(str, key, mode) {
      var temp = "";
      var salt = String.fromCharCode(48 - key);
      var saltText = "selamat belajar dan berusaha";
      var saltedStr = mode == 1 ? str : salt + str + saltText + key;
      console.log(saltedStr);
      for (var i = 0; i < saltedStr.length; i++) {
        var code = saltedStr.charCodeAt(i);
        if (!mode) {
          temp += String.fromCharCode((code + key) % 256);
        } else {
          temp += String.fromCharCode((code - key) % 256);
        }
      }
      return (this.result.soal1 = temp);
    },
    soal2(str, mode) {
      var temp = "";
      const saltText = "selamat belajar dan berusaha ";
      if (mode) {
        var saltedStr = str;
        var key = 1;
        console.log(temp + "=" + key);
        for (key; !temp.includes(saltText) && key < 100; key++) {
          var temp2 = "";
          for (let i = 0; i < saltedStr.length - 1; i++) {
            temp2 += String.fromCharCode(saltedStr.charCodeAt(i) ^ key % 256);
          }
          temp = temp2;
        }
        return (
          (this.result.soal2 = "Decrypted => " + temp),
          (this.input.key = key - 1)
        );
      } else {
        const key = Math.floor(Math.random() * 100);
        var saltedStr = key + str + saltText + " " + key + "" + key;
        console.log(saltedStr);
        for (let i = 0; i < saltedStr.length; i++) {
          temp += String.fromCharCode(saltedStr.charCodeAt(i) ^ key % 256);
        }
        console.log(key);
        return (this.result.soal2 = temp), (this.input.key = key);
      }
    },
    contoh5(str) {
      str = str.split("");
      var temp = str;
      while (temp.length % 8) {
        temp.push(" ");
      }
      console.log(temp);

      for (let i = 0; i < temp.length - 1; i += 8) {
        // console.log(i)
        for (let j = i; j < i + 8; j++) {
          switch (j % 8) {
            // case 3:
            case 3:
              [temp[j], temp[j + 1]] = [temp[j + 1], temp[j]];
              // console.log(j, temp[j], temp[j + 1]);
              break;
            case 0:
              [temp[j], temp[j + 7]] = [temp[j + 7], temp[j]];
              // console.log(j, temp[j], temp[j + 7]);
              break;
          }
        }
      }
      // console.log(temp);
      return (this.result.contoh5 = temp.join(""));
    }
  }
};
</script>
