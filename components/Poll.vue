<template>
  <div :class="{'container': true, 'loading': isLoading }">
    <div v-if="!submitted">
      <h1 class="title ">
        Formulari 1
      </h1>
      <b-alert v-if="errors.hasOwnProperty('ip')" show variant="danger" class="mb-4">
        ⚠️ {{ errors.ip }}
      </b-alert>
      <b-alert v-else-if="errors.hasOwnProperty('global')" show variant="danger" class="mb-4">
        ⚠️ {{ errors.global }}
      </b-alert>
      <b-alert v-else-if="Object.keys(errors).length > 0" show variant="danger" class="mb-4">
        ⚠️ {{ $t('form.errors') }}
      </b-alert>
      <b-form @submit.prevent="submitForm">
        <section class="form-section form-section-1">
          <b-form-group :label="$t('section1.title')">
            <b-form-checkbox-group id="checkbox-section-1" v-model="form.s1q1" name="s1q1">
              <b-form-checkbox v-for="(i) in Object.keys($t('section1')).length-1" :key="i" :value="i" :class="{'custom-control-selected' : form.s1q1.includes(i)}">
                {{ $t(`section1.op${i}`) }}
              </b-form-checkbox>
            </b-form-checkbox-group>
          </b-form-group>
        </section>

        <section class="form-section form-section-2">
          <b-form-group :label="$t('section2.title')">
            <div class="row">
              <b-form-group
                :label="$t('section2.q1')"
                label-for="s2q1"
                class="col-md-8"
              >
                <b-form-input
                  id="s2q1"
                  v-model="form.s2q1"
                  type="text"
                  size="lg"
                  required
                />
              </b-form-group>
              <b-form-group
                :label="$t('section2.q2')"
                label-for="s2q2"
                class="col-md-4"
              >
                <b-form-spinbutton id="s2q2" v-model="form.s2q2" min="1" max="10" />
              </b-form-group>
            </div>
            <div class="row">
              <b-form-group
                :label="$t('section2.q3')"
                label-for="s2q3"
                class="col-md-6"
                required
              >
                <b-form-radio v-model="form.s2q3" name="s2q3" value="1" :class="{'custom-control-selected' : form.s2q3 == 1}">
                  Si
                </b-form-radio>
                <b-form-radio v-model="form.s2q3" name="s2q3" value="0" :class="{'custom-control-selected' : form.s2q3 == 0}">
                  No
                </b-form-radio>
              </b-form-group>
              <transition name="fade">
                <b-form-group
                  v-if="form.s2q3 == 1"
                  :label="$t('section2.q4')"
                  label-for="s2q4"
                  class="col-md-6"
                  :required="form.s2q3 == 1"
                >
                  <b-form-spinbutton
                    id="s2q4"
                    v-model="form.s2q4"
                    min="1"
                    size="lg"
                  />
                </b-form-group>
              </transition>
            </div>
            <div class="row">
              <b-form-group
                :label="$t('section2.q5.q')"
                label-for="s2q5"
                class="col-md-6"
              >
                <b-form-radio
                  v-for="i in 4"
                  :key="i"
                  v-model="form.s2q5"
                  name="s2q5"
                  :value="i"
                  :class="{'custom-control-selected' : form.s2q5 == i}"
                >
                  {{ $t(`section2.q5.op${i}`) }}
                </b-form-radio>
              </b-form-group>
            </div>

            <h3>{{ $t('section2.subsection') }}</h3>
            <div class="row">
              <b-form-group
                :label="$t('section2.q6.q')"
                label-for="s2q6"
                class="col-md-6"
              >
                <b-form-radio
                  v-for="i in 3"
                  :key="i"
                  v-model="form.s2q6"
                  name="s2q6"
                  :value="i"
                  :class="{'custom-control-selected' : form.s2q6 == i}"
                >
                  {{ $t(`section2.q6.op${i}`) }}
                </b-form-radio>
              </b-form-group>
              <b-form-group
                :label="$t('section2.q7')"
                label-for="s2q7"
                class="col-md-6"
              >
                <b-form-spinbutton
                  id="s2q7"
                  v-model="form.s2q7"
                  min="1"
                  required
                />
              </b-form-group>
            </div>
            <div class="row">
              <b-form-group
                :label="$t('section2.q8')"
                label-for="s2q8"
                class="col-md-4"
              >
                <b-form-radio v-model="form.s2q8" name="s2q8" value="1" :class="{'custom-control-selected' : form.s2q8 == 1}">
                  Si
                </b-form-radio>
                <b-form-radio v-model="form.s2q8" name="s2q8" value="0" :class="{'custom-control-selected' : form.s2q8 == 0}">
                  No
                </b-form-radio>
              </b-form-group>
              <b-form-group
                :label="$t('section2.q9')"
                label-for="s2q9"
                class="col-md-4"
              >
                <b-form-radio v-model="form.s2q9" name="s2q9" value="1" :class="{'custom-control-selected' : form.s2q9 == 1}">
                  Si
                </b-form-radio>
                <b-form-radio v-model="form.s2q9" name="s2q9" value="0" :class="{'custom-control-selected' : form.s2q9 == 0}">
                  No
                </b-form-radio>
              </b-form-group>
              <b-form-group
                :label="$t('section2.q10')"
                label-for="s2q10"
                class="col-md-4"
              >
                <b-form-radio v-model="form.s2q10" name="s2q10" value="1" :class="{'custom-control-selected' : form.s2q10 == 1}">
                  Si
                </b-form-radio>
                <b-form-radio v-model="form.s2q10" name="s2q10" value="0" :class="{'custom-control-selected' : form.s2q10 == 0}">
                  No
                </b-form-radio>
              </b-form-group>
            </div>
          </b-form-group>
        </section>

        <section class="form-section form-section-3">
          <b-form-group :label="$t('section3.title')">
            <div class="row">
              <b-form-group
                :label="$t('section3.q1.q')"
                label-for="s3q1"
                class="col-md-6"
              >
                <b-form-radio
                  v-for="i in 5"
                  :key="i"
                  v-model="form.s3q1"
                  name="s3q1"
                  :value="i"
                  :class="{'custom-control-selected' : form.s3q1 == i}"
                >
                  {{ $t(`section3.q1.op${i}`) }}
                </b-form-radio>
              </b-form-group>
            </div>
            <b-form-group
              :label="$t('section3.q2')"
              labclass="col-md-6"
              label-for="s3q2"
            >
              <b-form-spinbutton
                id="s3q2"
                v-model="form.s3q2"
                min="1"
              />
            </b-form-group>
            <div class="row">
              <b-form-group
                :label="$t('section3.q3')"
                label-for="s3q3"
                class="col-md-6"
              >
                <b-form-radio v-model="form.s3q3" name="s3q3" value="1" :class="{'custom-control-selected' : form.s3q3 == 1}">
                  Si
                </b-form-radio>
                <b-form-radio v-model="form.s3q3" name="s3q3" value="0" :class="{'custom-control-selected' : form.s3q3 == 0}">
                  No
                </b-form-radio>
              </b-form-group>
              <transition name="fade">
                <b-form-group
                  v-if="form.s3q3 == 1"
                  :label="$t('section3.q4')"
                  label-for="s3q4"
                  class="col-md-6"
                  :required="form.s3q3 == 1"
                >
                  <b-form-spinbutton
                    id="s3q4"
                    v-model="form.s3q4"
                    min="1"
                  />
                </b-form-group>
              </transition>
            </div>
            <div class="row">
              <b-form-group
                :label="$t('section3.q5.q')"
                label-for="s3q5"
                class="col-md-6"
              >
                <b-form-radio
                  v-for="i in 3"
                  :key="i"
                  v-model="form.s3q5"
                  name="s3q5"
                  :value="i"
                  :class="{'custom-control-selected' : form.s3q5 == i}"
                >
                  {{ $t(`section3.q5.op${i}`) }}
                </b-form-radio>
              </b-form-group>
            </div>
            <transition name="fade">
              <template v-if="form.s3q5 > 1">
                <div class="row">
                  <b-form-group
                    :label="$t('section3.subsection1.q2')"
                    label-for="s3q6x1"
                    class="col-md-4"
                    :required="form.s3q5 > 1"
                  >
                    <b-form-radio
                      v-for="i in 2"
                      :key="i"
                      v-model="form.s3q6x1"
                      name="s3q6x1"
                      :value="i"
                      :class="{'custom-control-selected' : form.s3q6x1 == i}"
                    >
                      {{ $t(`section3.subsection1.q1.op${i}`) }}
                    </b-form-radio>
                  </b-form-group>
                  <b-form-group
                    :label="$t('section3.subsection1.q2')"
                    label-for="s3q6x2"
                    class="col-md-4"
                    :required="form.s3q5 > 1"
                  >
                    <b-form-radio v-model="form.s3q6x2" name="s3q6x2" value="1" :class="{'custom-control-selected' : form.s3q6x2 == 1}">
                      Si
                    </b-form-radio>
                    <b-form-radio v-model="form.s3q6x2" name="s3q6x2" value="0" :class="{'custom-control-selected' : form.s3q6x2 == 0}">
                      No
                    </b-form-radio>
                  </b-form-group>
                  <b-form-group
                    :label="$t('section3.subsection1.q3')"
                    label-for="s3q6x3"
                    class="col-md-4 money-input"
                    :required="form.s3q5 > 1"
                  >
                    <b-input-group append="€">
                      <b-form-input
                        id="s3q6x3"
                        v-model="form.s3q6x3"
                        type="text"
                        size="lg"
                      />
                    </b-input-group>
                  </b-form-group>
                </div>
              </template>
            </transition>
            <h3>{{ $t('section3.subsection2') }}</h3>
            <div class="row">
              <b-form-group
                :label="$t('section3.q8')"
                label-for="s3q8"
                class="col-md-4"
              >
                <b-form-radio v-model="form.s3q8" name="s3q8" value="1" :class="{'custom-control-selected' : form.s3q8 == 1}">
                  Si
                </b-form-radio>
                <b-form-radio v-model="form.s3q8" name="s3q8" value="0" :class="{'custom-control-selected' : form.s3q8 == 0}">
                  No
                </b-form-radio>
              </b-form-group>
              <b-form-group
                :label="$t('section3.q9')"
                label-for="s3q9"
                class="col-md-4"
              >
                <b-form-radio v-model="form.s3q9" name="s3q9" value="1" :class="{'custom-control-selected' : form.s3q9 == 1}">
                  Si
                </b-form-radio>
                <b-form-radio v-model="form.s3q9" name="s3q9" value="0" :class="{'custom-control-selected' : form.s3q9 == 0}">
                  No
                </b-form-radio>
              </b-form-group>
              <b-form-group
                :label="$t('section3.q7')"
                label-for="s3q7"
                class="col-md-4"
              >
                <b-form-spinbutton
                  id="s3q7"
                  v-model="form.s3q7"
                  min="1"
                  required
                />
              </b-form-group>
            </div>
            <div class="row">
              <b-form-group
                :label="$t('section3.q10')"
                label-for="s3q10"
                class="col-md-4"
              >
                <b-form-radio v-model="form.s3q10" name="s3q10" value="1" :class="{'custom-control-selected' : form.s3q10 == 1}">
                  Si
                </b-form-radio>
                <b-form-radio v-model="form.s3q10" name="s3q10" value="0" :class="{'custom-control-selected' : form.s3q10 == 0}">
                  No
                </b-form-radio>
              </b-form-group>
              <b-form-group
                :label="$t('section3.q11.q')"
                label-for="s3q11"
                class="col-md-4"
              >
                <b-form-radio
                  v-for="i in 3"
                  :key="i"
                  v-model="form.s3q11"
                  name="s3q11"
                  :value="i"
                  :class="{'custom-control-selected' : form.s3q11 == i}"
                >
                  {{ $t(`section3.q11.op${i}`) }}
                </b-form-radio>
              </b-form-group>
            </div>
          </b-form-group>
        </section>
        <div class="form-buttons">
          <b-button variant="primary" size="lg" type="submit" :class="{'disabled' : errors.hasOwnProperty('ip'), 'submit-btn' : true}">
            ✉️ {{ $t('form.button') }}
          </b-button>
        </div>
      </b-form>
    </div>
    <b-alert v-else show variant="success" class="mb-4">
      ✔️ La teua resposta s'ha enviat correctament.
    </b-alert>
  </div>
</template>

<script>
export default {
  name: 'Poll',

  data () {
    return {
      form: {
        s1q1: [],
        s2q1: null,
        s2q2: null,
        s2q3: null,
        s2q4: null,
        s2q5: null,
        s2q6: null,
        s2q7: null,
        s2q8: null,
        s2q9: null,
        s2q10: null,
        s3q1: null,
        s3q2: null,
        s3q3: null,
        s3q4: null,
        s3q5: null,
        s3q6x1: null,
        s3q6x2: null,
        s3q6x3: null,
        s3q7: null,
        s3q8: null,
        s3q9: null,
        s3q10: null
      },
      isLoading: false,
      errors: [],
      submitted: false
    }
  },
  methods: {
    submitForm () {
      this.isLoading = true

      this.$axios({
        url: 'https://sillaparticipa.com/2020/api/form/register/?lang=' + this.$i18n.locale,
        method: 'POST',
        headers: {
          'Content-Type': 'application/x-www-form-urlencoded'
        },
        data: this.encode(this.form)
      }).then((response) => {
        return response.json()
      }).then((response) => {
        if (response.success) {
          this.submitted = true
        } else {
          this.errors = response.errors
        }
      }).catch(() => {
        this.errors = {
          global: this.$t('form.servererror')
        }
      }).then(() => {
        window.scrollTo({
          top: 0,
          behavior: 'smooth'
        })
        this.isLoading = false
      })
    },

    encode (data) {
      return Object.keys(data)
        .map(
          key => `${encodeURIComponent(key)}=${data[key] ? encodeURIComponent(data[key]) : ''}`
        )
        .join('&')
    }
  }
}
</script>

<style lang="scss">
@import '../sass/variables';

h3 {
  font-size: 1.25rem;
  margin-top: 2.5rem;
}

.title {
  color: $primary;
  padding: 2rem;
  background-color: lighten($primary, 40);
  border-radius: $border-radius-lg;
}

.form-section {
  margin-bottom: 1rem;
  padding: 2rem;
}

.col-form-label {
  color: $primary;
  font-size: 1.5rem;
  font-weight: bold;
}

.custom-control {
  padding-left: 0;

  &-inline {
    margin-right: 0;
  }
}

.d-block {
  margin-top: 1.5rem;
}

.money-input {
  .input-group {
    width: 12rem;
  }

  .form-control {
    text-align: right;
  }

  .input-group-text {
    border-top-right-radius: $border-radius-lg;
    border-bottom-right-radius: $border-radius-lg;
    font-size: 1.5rem;
  }

  &:focus-within .input-group-text {
    background: lighten($primary, 40);
    color: $primary;
    border-color: #f2b5b5 !important; // shame on guillem
    box-shadow: 0 0 0 0.2rem rgba(224, 72, 72, 0.25); // shame on guillem
  }
}

.custom-control-label {
  display: flex;
  align-items: center;
  transition: 0.25s ease-in-out;
  padding: 1.25rem 1.5rem 1.25rem 2.5rem;
  border: 1.75px solid transparent;
  background: white;
  box-shadow: $default-shadow;
  border-radius: $border-radius-lg;
  cursor: pointer;
  margin: 0.5rem 1rem 0.5rem 0;

  &::before, &::after {
    position: absolute;
    top: 1.5rem;
    left: 1rem;
  }

  &:hover {
    text-decoration: none;
    transform: translateY(-.15rem);
    box-shadow: $raised-shadow;
    color: #000;
  }
}

.custom-control-selected {
  .custom-control-label {
    border-color: $primary;
    color: $primary;
    background: lighten($primary, 40);
  }
}

.form-buttons {
  margin-bottom: 3rem;
  display: flex;
  font-weight: bold;
  justify-content: center;

  .submit-btn {
    margin-right: 1rem;
    max-width: 800px;
    width: 100%;
  }
}

.form-control-lg {
  padding: 2.05rem 1rem;
  font-size: 1.5rem;
}

.fade-enter-active, .fade-leave-active {
  transition: .4s ease-in-out;
  max-height: 1000px;
}

.fade-enter, .fade-leave-to {
  max-height: 0;
  transform: translateY(-3rem);
  opacity: 0;
}

// disgusting, shame on you boostrap-vue
.b-form-spinbutton.form-control {
  width: 12rem;
  font-size: 2.25rem;
  padding: 0.75rem;
  border-radius: $border-radius-lg;
}

.b-form-spinbutton.form-control.focus {
  border-color: #f2b5b5 !important;
  box-shadow: 0 0 0 0.2rem rgba(224, 72, 72, 0.25);
}

.alert {
  font-size: 1.5rem;
}
</style>
