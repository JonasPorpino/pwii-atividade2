<template>
  <div class="container mt-2">
    <b-form>
      <b-form-group
        label="Contato"
        label-for="subject"
      >
        <b-form-input
          id="subject"
          v-model="form.subject"
          type="text"
          placeholder="Nome do Contato"
          required
          autocomplete="off"
        ></b-form-input>
      </b-form-group>

      <b-form-group
        label="Contato Telefone ou E-mail"
        label-for="description"
      >
        <b-form-textarea
          id="description"
          v-model="form.description"
          type="text"
          placeholder="Telefone"
          required
          autocomplete="off"
        ></b-form-textarea>
      </b-form-group>

      <b-button type="submit" variant="outline-primary" @click="saveTask"> Salvar </b-button>
    </b-form>
  </div>
</template>

<script>
import ToastMixin from "@/mixins/toastMixin.js";

export default {
  name: "Form",

  mixins: [ToastMixin],

  data() {
    return {
      form: {
        subject: "",
        description: ""
      },
      methodSave: "new"
    }
  },

  created() {
    if(this.$route.params.index === 0 || this.$route.params.index !== undefined){
      this.methodSave = "update";
      let tasks = JSON.parse(localStorage.getItem("tasks"));
      this.form = tasks[this.$route.params.index];
    }
  },

  methods: {
    saveTask() {
      if(this.methodSave === "update"){
        let tasks = JSON.parse(localStorage.getItem("tasks"));
        tasks[this.$route.params.index] = this.form;
        localStorage.setItem("tasks", JSON.stringify(tasks));
        this.showToast("success", "Sucesso!", "Contato Atualizado com suceso");
        this.$router.push({ name: "list" });
        return;
      }

      let tasks = (localStorage.getItem("tasks")) ? JSON.parse(localStorage.getItem("tasks")) : [];
      tasks.push(this.form);
      localStorage.setItem("tasks", JSON.stringify(tasks));
      this.showToast("success", "Sucesso!", "Contato criado com suceso");
      this.$router.push({ name: "list" });
    }
  }
}
</script>
