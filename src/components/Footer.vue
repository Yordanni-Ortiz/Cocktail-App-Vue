<script>
export default {
  name: 'Footer',
  data() {
    return {
      wts: "https://api.whatsapp.com/send/?phone=584126351466&text=Hola%2C+%C2%A1Mucho+gusto%21%0AGracias+por+escribir.%0A%C2%BFEn+qu%C3%A9+puedo+ayudarte%3F&type=phone_number&app_absent=0",
      mail: "https://mail.google.com/mail/u/0/?view=cm&fs=1&to=yordannimod@gmail.com",
      linkedIn: "https://www.linkedin.com/in/yordanni-ortiz/",
    };
  },
};
</script>

<template>
  <div class="footer">
    <article class="one">
        <img :src="'/LogoCompleto.png'" class="logo" alt="Logo" />
      <div class="thanks">
        <img :src="'/coctel-footer.png'" class="coctel-icon" alt="Coctel" />
        <p class="container-title">
          Cocktail App
        </p>
      </div>
    </article>
    <article class="two">
      <p class="container-title">
        ¡Gracias por visitar mi página web, espero que podamos trabajar juntos próximamente!
      </p>
      <div class="thanks">
        <span>
          Si deseas contactarme, puedes hacerlo a través del formulario o de
          mi correo electrónico
          <a :href="mail" target="_blank">
            yordannimod@gmail.com
          </a>
          y también puedes seguirme en
          <a :href="linkedIn" target="_blank">
            LinkedIn
          </a>
          para mantenerte informado sobre mis últimas actualizaciones y proyectos.
        </span>
      </div>
      <div class="year">
        © 2023 - todos los derechos reservados
      </div>
    </article>
    <article class="three">
      <p class="container-title">
        Contacto
      </p>
      <div class="icon-container">
        <a :href="linkedIn" target="_blank">
          <img src="/linkedin.png" alt="" />
        </a>
        <a :href="mail" target="_blank">
          <img src="/gmail.png" alt="" />
        </a>
        <a :href="wts" target="_blank">
          <img src="/whatsapp.png" alt="" />
        </a>
      </div>
    </article>
  </div>
</template>

<style>
  @import url('../assets/styles/Footer.css');
</style>