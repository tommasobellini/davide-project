<!-- Please remove this file from your project -->
<template>
  <div
    class="relative flex items-top justify-center min-h-screen  sm:items-center sm:pt-0"
  >
    <link
      href="https://cdn.jsdelivr.net/npm/tailwindcss@2.1.2/dist/tailwind.min.css"
      rel="stylesheet"
    />
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
      <div class="mt-8 bg-white overflow-hidden  p-6">
        <div style="width: 100vh; padding: 5px;">
          <b-form @submit="onSubmit" @reset="onReset" v-if="show">
            <b-form-group
              v-if="!url"
              id="input-group-1"
              label="Logo:"
              label-for="input-1"
            >
              <b-form-file
                id="input-1"
                v-model="form.logo"
                placeholder="Choose a file or drop it here..."
                drop-placeholder="Drop file here..."
                required
                @change="onFileChange"
              ></b-form-file>

            </b-form-group>
            <div id="preview">
              <img v-if="url" :src="url" />
            </div>
          <b-form-group
            id="input-group-1"
            label="Titolo dell'opera:"
            label-for="input-1"
          >
            <b-form-input
              id="input-1"
              v-model="form.title"
              placeholder="Inserisci titolo.."
              required
            ></b-form-input>
          </b-form-group>

            <b-form-group id="input-group-2" label="Data:" label-for="input-2">
              <b-form-datepicker
                id="input-2"
                v-model="form.date"
                placeholder="Inserisci data.."
                required
              ></b-form-datepicker>
            </b-form-group>

            <b-form-group id="input-group-3" label="Luogo:" label-for="input-3">
              <b-form-input
                id="input-3"
                v-model="form.location"
                placeholder="Inserisci luogo.."
                required
              ></b-form-input>
            </b-form-group>
            <b-form-group id="input-group-3" label="Descrizione:" label-for="input-3">
              <b-form-textarea
                id="input-3"
                v-model="form.description"
                placeholder="Inserisci descrizione.."
                rows="3"
                required
              ></b-form-textarea>
            </b-form-group>
            <b-form-group id="input-group-3" label="Fasi di Lavoro:" label-for="input-3">
              <b-form-textarea
                id="input-3"
                v-model="form.work_steps"
                placeholder="Inserisci fasi di lavoro.."
                rows="5"
                required
              ></b-form-textarea>
            </b-form-group>

            <b-form-group id="input-group-3" label="Materiali:" label-for="input-3">
              <b-form-textarea
                id="input-3"
                v-model="form.materials"
                placeholder="Inserisci materiali usati.."
                rows="5"
                required
              ></b-form-textarea>
            </b-form-group>
            <b-form-group id="input-group-3" label="Preventivo:" label-for="input-3">
              <b-form-textarea
                id="input-3"
                v-model="form.billing"
                placeholder="Inserisci preventivo.."
                rows="5"
                required
              ></b-form-textarea>
            </b-form-group>

            <b-button type="submit" variant="primary">Stampa</b-button>
          </b-form>
        </div>

      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'ProjectForm',
    data() {
      return {
        url: null,
        form: {
          logo: null,
          title: '',
          date: '',
          location: '',
          description: '',
          work_steps: '',
          materials: '',
          billing: ''
        },
        show: true
      }
    },
    methods: {
      onFileChange(e) {
        const file = e.target.files[0];
        this.url = URL.createObjectURL(file);
      },
      onSubmit(event) {
        event.preventDefault()
        window.print()
      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        // this.form.email = ''
        // this.form.name = ''
        // this.form.food = null
        // this.form.checked = []
        // // Trick to reset/clear native browser form validation state
        // this.show = false
        // this.$nextTick(() => {
        //   this.show = true
        // })
      }
  }
}
</script>

<style>
#preview {
  display: flex;
}

#preview img {
  max-width: 100%;
  max-height: 250px;
}
</style>
