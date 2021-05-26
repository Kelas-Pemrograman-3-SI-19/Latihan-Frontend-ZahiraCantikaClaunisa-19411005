<template>
    <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="form.namaKegiatan"
        label="Nama Kegiatan *"
        :rules="[ val => val && val.length > 0 || 'Mohon Isi Nama Kegiatan']"
      />
        <q-input
        filled
        v-model="form.deskripsi"
        label="Deskrpsi Kegiatan *"
        :rules="[ val => val && val.length > 0 || 'Mohon Isi Deskripsi Kegiatan']"
      />
        <q-input
        filled
        v-model="form.waktu"
        label="Waktu Kegiatan *"
        :rules="[ val => val && val.length > 0 || 'Mohon Isi Waktu Kegiatan']"
      />

      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
      </div>
    </q-form>

  </div>
</template>

<script>

export default{
  data () {
    return {
      form: {
        namaKegiatan: null,
        deskripsi: null,
        waktu: null
      }
    } 
  },
  methods: {
    onSubmit () {
      this.$axios.post('kegiatan/insert', this.form)
      .then(res => {
        console.log(res)
      }).catch(e => {
            console.log(e)
          })
    }
  },
}
</script>
