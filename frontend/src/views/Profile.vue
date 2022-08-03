<template>
  <div class="card">
    <h1 class="card__title">Vente</h1>
    <p class="card__subtitle">Bienvenue dans notre espace de vente d'articles</p>
    <p class="card__site">Pour plus d'information sur le site veuillez </p>
    <p class="card__lien" ><a  href="https://lamis-boutique.fr/fr/nouveaux-produits">Consulter le site</a></p>
    <p>{{user.prenom}} {{user.nom}} {{user.email}}</p>
    <p class="card__photo">
      <img  :src="require('@/assets/logo2.jpg')"/>
   </p>
    <div class="form-row">
      <button @click="logout()" class="button">
        Déconnexion
      </button>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'Profile',
  mounted: function () {
    console.log(this.$store.state.user);
    if (this.$store.state.user.userId == -1) {
      this.$router.push('/');
      return ;
    }
    this.$store.dispatch('getUserInfos');
  },
  computed: {
    ...mapState({
      user: 'userInfos',
    })
  },
  methods: {
    logout: function () {
      this.$store.commit('logout');
      this.$router.push('/');
    }
  }
}
</script>

<style scoped>

</style>>
