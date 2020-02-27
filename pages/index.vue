<template>
  <div class="container">
    <h1 class="title">
      Silla Participa
    </h1>
    <b-form-group :label="$t('section1.title')">
      <b-form-checkbox-group id="checkbox-section-1" v-model="s1q1" name="flavour-2">
        <b-form-checkbox v-for="(i) in Object.keys(langStrings.ca.section1).length-1" :key="i" :value="i">
          {{ $t(`section1.op${i}`) }}
        </b-form-checkbox>
      </b-form-checkbox-group>
    </b-form-group>

    <b-form-group :label="$t('section2.title')">
      <b-form-group
        :label="$t('section2.q1')"
        label-for="s2q1"
      >
        <b-form-input
          id="s2q1"
          v-model="s2q1"
          type="text"
          required
        />
      </b-form-group>
      <b-form-group
        :label="$t('section2.q2')"
        label-for="s2q2"
      >
        <b-form-input
          id="s2q2"
          v-model="s2q2"
          type="number"
          required
        />
      </b-form-group>
      <b-form-group
        :label="$t('section2.q3')"
        label-for="s2q3"
      >
        <b-form-radio v-model="s2q3" name="s2q3-yes" value="1">
          Si
        </b-form-radio>
        <b-form-radio v-model="s2q3" name="s2q3-no" value="0">
          No
        </b-form-radio>
      </b-form-group>
      <b-form-group
        v-if="s2q3 == 1"
        :label="$t('section2.q4')"
        label-for="s2q4"
      >
        <b-form-input
          id="s2q4"
          v-model="s2q4"
          type="number"
        />
      </b-form-group>
      <b-form-group
        :label="$t('section2.q5.q')"
        label-for="s2q5"
      >
        <b-form-radio v-for="i in 4" :key="i" v-model="s2q5" :name="'s2q5-'+i" :value="i">
          {{ $t(`section2.q5.op${i}`) }}
        </b-form-radio>
      </b-form-group>
      <h3>{{ $t('section2.subsection') }}</h3>
      <b-form-group
        :label="$t('section2.q6.q')"
        label-for="s2q6"
      >
        <b-form-radio v-for="i in 3" :key="i" v-model="s2q6" :name="'s2q6-'+i" :value="i">
          {{ $t(`section2.q6.op${i}`) }}
        </b-form-radio>
      </b-form-group>
      <b-form-group
        :label="$t('section2.q7')"
        label-for="s2q7"
      >
        <b-form-input
          id="s2q7"
          v-model="s2q7"
          type="number"
          required
        />
      </b-form-group>
      <b-form-group
        :label="$t('section2.q8')"
        label-for="s2q8"
      >
        <b-form-radio v-model="s2q8" name="s2q8-yes" value="1">
          Si
        </b-form-radio>
        <b-form-radio v-model="s2q8" name="s2q8-no" value="0">
          No
        </b-form-radio>
      </b-form-group>
      <b-form-group
        :label="$t('section2.q9')"
        label-for="s2q9"
      >
        <b-form-radio v-model="s2q9" name="s2q9-yes" value="1">
          Si
        </b-form-radio>
        <b-form-radio v-model="s2q9" name="s2q9-no" value="0">
          No
        </b-form-radio>
      </b-form-group>
      <b-form-group
        :label="$t('section2.q10')"
        label-for="s2q10"
      >
        <b-form-radio v-model="s2q10" name="s2q10-yes" value="1">
          Si
        </b-form-radio>
        <b-form-radio v-model="s2q10" name="s2q10-no" value="0">
          No
        </b-form-radio>
      </b-form-group>
    </b-form-group>
    <b-form-group :label="$t('section3.title')">
      <b-form-group
        :label="$t('section3.q1.q')"
        label-for="s3q1"
      >
        <b-form-radio v-for="i in 5" :key="i" v-model="s3q1" :name="'s3q1-'+i" :value="i">
          {{ $t(`section3.q1.op${i}`) }}
        </b-form-radio>
      </b-form-group>
      <b-form-group
        :label="$t('section3.q2')"
        label-for="s3q2"
      >
        <b-form-input
          id="s3q2"
          v-model="s3q2"
          type="number"
        />
      </b-form-group>
      <b-form-group
        :label="$t('section3.q3')"
        label-for="s3q3"
      >
        <b-form-radio v-model="s3q3" name="s3q3-yes" value="1">
          Si
        </b-form-radio>
        <b-form-radio v-model="s3q3" name="s3q3-no" value="0">
          No
        </b-form-radio>
      </b-form-group>
      <b-form-group
        v-if="s3q3 == 1"
        :label="$t('section3.q4')"
        label-for="s3q4"
      >
        <b-form-input
          id="s3q4"
          v-model="s3q4"
          type="number"
        />
      </b-form-group>
      <b-form-group
        :label="$t('section3.q5.q')"
        label-for="s3q5"
      >
        <b-form-radio v-for="i in 3" :key="i" v-model="s3q5" :name="'s3q5-'+i" :value="i">
          {{ $t(`section3.q5.op${i}`) }}
        </b-form-radio>
      </b-form-group>
      <h3>{{ $t('section3.subsection1.title') }}</h3>
      <b-form-group>
        <b-form-radio v-for="i in 2" :key="i" v-model="s3q6x1" :name="'s3q6x1-'+i" :value="i">
          {{ $t(`section3.subsection1.q1.op${i}`) }}
        </b-form-radio>
      </b-form-group>
      <b-form-group
        :label="$t('section3.subsection1.q2')"
        label-for="s3q6x2"
      >
        <b-form-radio v-model="s3q6x2" name="s3q6x2-yes" value="1">
          Si
        </b-form-radio>
        <b-form-radio v-model="s3q6x2" name="s3q6x2-no" value="0">
          No
        </b-form-radio>
      </b-form-group>
      <b-form-group
        :label="$t('section3.subsection1.q3')"
        label-for="s3q6x3"
      >
        <b-form-input
          id="s3q6x3"
          v-model="s3q6x3"
          type="number"
        />
      </b-form-group>
      <h3>{{ $t('section3.subsection2') }}</h3>
      <b-form-group
        :label="$t('section3.q7')"
        label-for="s3q7"
      >
        <b-form-input
          id="s3q7"
          v-model="s3q7"
          type="number"
          required
        />
      </b-form-group>
      <b-form-group
        :label="$t('section3.q8')"
        label-for="s3q8"
      >
        <b-form-radio v-model="s3q8" name="s3q8-yes" value="1">
          Si
        </b-form-radio>
        <b-form-radio v-model="s3q8" name="s3q8-no" value="0">
          No
        </b-form-radio>
      </b-form-group>
      <b-form-group
        :label="$t('section3.q9')"
        label-for="s3q9"
      >
        <b-form-radio v-model="s3q9" name="s3q9-yes" value="1">
          Si
        </b-form-radio>
        <b-form-radio v-model="s3q9" name="s3q9-no" value="0">
          No
        </b-form-radio>
      </b-form-group>
      <b-form-group
        :label="$t('section3.q10')"
        label-for="s3q10"
      >
        <b-form-radio v-model="s3q10" name="s3q10-yes" value="1">
          Si
        </b-form-radio>
        <b-form-radio v-model="s3q10" name="s3q10-no" value="0">
          No
        </b-form-radio>
      </b-form-group>
      <b-form-group
        :label="$t('section3.q11.q')"
        label-for="s3q11"
      >
        <b-form-radio v-for="i in 3" :key="i" v-model="s3q11" name="s3q11" :value="i">
          {{ $t(`section3.q11.op${i}`) }}
        </b-form-radio>
      </b-form-group>
    </b-form-group>
  </div>
</template>

<script>
import langStrings from '../i18n/langStrings'

export default {
  data () {
    return {
      langStrings,
      s1q1: [],
      s2q1: '',
      s2q2: '',
      s2q3: '',
      s2q4: '',
      s2q5: '',
      s2q6: '',
      s2q7: '',
      s2q8: '',
      s2q9: '',
      s2q10: '',
      s3q1: '',
      s3q2: '',
      s3q3: '',
      s3q4: '',
      s3q5: '',
      s3q6x1: '',
      s3q6x2: '',
      s3q6x3: '',
      s3q7: '',
      s3q8: '',
      s3q9: '',
      s3q10: ''
    }
  }
}
</script>

<style>
</style>
