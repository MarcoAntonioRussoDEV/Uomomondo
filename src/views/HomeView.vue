<template>
  <Hero />
  <main id="home" class="container">
    <Section>
      <div class="flex flex-col items-center gap-2">
        <img class="h-24" src="@/assets/logo-marconi.svg" alt="Logo Istituto Marconi" />
        <p>Progetto per l'educazione alla PACE</p>
      </div>
    </Section>
    <Section data-aos="fade-left" data-aos-anchor-placement="top-center">
      <Card cardTitle="title" :imgSrc="imgUrl" reverse>
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Perferendis facere sint minus
        veritatis itaque quaerat doloribus, cumque nihil tenetur eius libero, a reiciendis omnis.
        Ullam perspiciatis consequuntur iste architecto? Asperiores.
      </Card>
    </Section>
    <Section>
      <h2 data-aos="zoom-in" class="text-6xl">Il Team</h2>
      <div class="grid grid-cols-2 md:grid-cols-3 xl:grid-cols-5">
        <Avatar
          data-aos="zoom-in"
          data-aos-anchor-placement="top-center"
          v-for="prof in professors"
          :imgSrc="prof.imgUrl"
        >
          <div class="flex flex-col items-center text-center">
            <h3 class="font-bold">{{ prof.name }}</h3>
            <small>{{ prof.role }}</small>
          </div>
        </Avatar>
      </div>
    </Section>
    <Section>
      <CardText cardTitle="Contatti" class="bg-primary text-primary-content">
        <div class="flex justify-evenly items-center mt-10">
          <a v-for="social in socials" target="_blank" :href="social.link">
            <Icon :icon="social.icon" class="text-5xl" />
          </a>
        </div>
      </CardText>
    </Section>
  </main>
</template>

<script>
import Hero from '@/components/Hero.vue'
import Section from '@/components/Section.vue'
import Card from '@/components/Card.vue'
import Avatar from '@/components/Avatar.vue'
import imgUrl from '@/assets/images/1.png'
import imgMQ from '@/assets/images/michele-quintana.jpg'
import { Icon } from '@iconify/vue'
import CardText from '@/components/CardText.vue'

const professors = [
  {
    name: 'Prof. Michele Quintana',
    role: 'Responsabile di progetto',
    imgUrl: imgMQ,
  },
  {
    name: 'Prof. Luigi Paparesta',
    role: 'Docente collaboratore',
    imgUrl: 'https://avatar.iran.liara.run/public/job/teacher/male',
  },
  {
    name: 'Prof.ssa Anna Rignanese',
    role: 'Docente collaboratore',
    imgUrl: 'https://avatar.iran.liara.run/public/job/teacher/female',
  },
  {
    name: 'Prof.ssa Antonella Lopopolo',
    role: 'Docente collaboratore',
    imgUrl: 'https://avatar.iran.liara.run/public/job/teacher/female',
  },
  {
    name: 'Prof.ssa  Monica Gigante',
    role: 'Docente collaboratore',
    imgUrl: 'https://avatar.iran.liara.run/public/job/teacher/female',
  },
  {
    name: 'Prof. Antonio Pece',
    role: 'Docente collaboratore',
    imgUrl: 'https://avatar.iran.liara.run/public/job/teacher/male',
  },
  {
    name: 'Prof. Francesco Lorusso',
    role: 'Docente collaboratore',
    imgUrl: 'https://avatar.iran.liara.run/public/job/teacher/male',
  },
  {
    name: 'Prof. Giuseppe La Porta',
    role: 'Docente collaboratore esterno',
    imgUrl: 'https://avatar.iran.liara.run/public/job/teacher/male',
  },
  {
    name: 'Prof.  Ciro Quirino',
    role: 'Docente collaboratore esterno',
    imgUrl: 'https://avatar.iran.liara.run/public/job/teacher/male',
  },
  {
    name: 'Prof.ssa  Carla Bonfitto',
    role: 'Docente collaboratore esterno',
    imgUrl: 'https://avatar.iran.liara.run/public/job/teacher/female',
  },
]
const socials = [
  {
    icon: 'mdi:instagram',
    link: 'https://www.instagram.com/uomomondo_marconi',
  },
  {
    icon: 'material-symbols:mail-outline',
    link: 'mailto:uomomondo510@gmail.com',
  },

  {
    icon: 'mdi:youtube',
    link: 'https://www.youtube.com/channel/UCLg2Dyj_7zlSk4tiQMgRHcQ/featured',
  },
  {
    icon: 'mdi:web',
    link: 'https://www.google.com/url?q=https%3A%2F%2Fwww.liceogmarconifg.edu.it%2F&sa=D&sntz=1&usg=AOvVaw0xX2BPxy_oVDMjTVetbQ7D',
  },
  {
    icon: 'mdi:youtube',
    link: 'https://www.youtube.com/watch?v=2_LH-xu_Uqo',
  },
]

export default {
  components: {
    Hero,
    Section,
    Card,
    Avatar,
    Icon,
    CardText,
  },
  data() {
    return {
      imgUrl,
      professors,
      socials,
    }
  },
}
</script>
<style scoped></style>
