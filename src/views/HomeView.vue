<template>
  <div>
    <Section>
      <Hero />
    </Section>
    <main id="home" class="container mx-auto px-4">
      <Section>
        <InfiniteScrollHorizontal />
      </Section>
      <Section data-aos="fade-left" data-aos-anchor-placement="top-center">
        <Card
          cardTitle="title"
          class="bg-accent"
          :imgSrc="imgUrl"
          reverse
          collapse
          :collapseContent="collapseContent"
        >
          Lorem ipsum dolor sit amet consectetur, adipisicing elit. Perferendis facere sint minus
          veritatis itaque quaerat doloribus, cumque nihil tenetur eius libero, a reiciendis omnis.
          Ullam perspiciatis consequuntur iste architecto? Asperiores.
        </Card>
      </Section>
      <Section>
        <h2 data-aos="zoom-in" class="text-6xl font-bold">Il Team</h2>
        <div class="grid grid-cols-2 md:grid-cols-3 xl:grid-cols-5">
          <Avatar
            data-aos="zoom-in"
            data-aos-anchor-placement="bottom-bottom"
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
        <Card
          cardTitle="Il Progetto"
          imgSrc="/walk.png"
          class="bg-primary"
          button-text="Unisciti a noi"
          reverse
          data-aos="zoom-in"
        >
          <p>
            Il progetto si prefigge di sensibilizzare tutto l’Istituto sulle tematiche relative alla
            <strong>pace</strong> (ci piace declinare l’educazione alla pace come intercultura,
            convivenza tra i popoli, cittadinanza attiva, difesa dei diritti dell’uomo, educazione
            alla corresponsabilità sociale e alla legalità, attenzione all’ambito sociale e
            all’ambiente, al bene comune, al volontariato, alla solidarietà) e, in particolare,
            cerca di formare una coscienza critica su questi argomenti nei ragazzi che partecipano
            al Progetto, affinchè ne diventino promotori presso i loro compagni.
          </p>
          <p>
            Questo per far crescere il livello di cittadinanza attiva e di tutte le competenze di
            cittadinanza e di educazione civica in generale.
          </p>
        </Card>
      </Section>
      <Section>
        <CardText cardTitle="Contatti" class="bg-base-200" data-aos="fade-up">
          <div class="flex justify-evenly items-center mt-10">
            <a
              class="group flex flex-col items-center relative"
              v-for="social in socials"
              target="_blank"
              :href="social.link"
            >
              <Icon
                :icon="social.icon"
                class="text-5xl group-hover:-translate-y-full duration-300"
              />
              <span
                class="text-sm hidden group-hover:inline group-hover:absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 text-nowrap"
                >{{ social?.caption }}</span
              >
            </a>
          </div>
        </CardText>
      </Section>
    </main>
  </div>
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
import InfiniteScrollHorizontal from '@/components/InfiniteScrollHorizontal.vue'
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
    caption: '@uomomondo_marconi',
  },
  {
    icon: 'material-symbols:mail-outline',
    link: 'mailto:uomomondo510@gmail.com',
    caption: 'uomomondo510@gmail.com',
  },

  {
    icon: 'mdi:youtube',
    link: 'https://www.youtube.com/channel/UCLg2Dyj_7zlSk4tiQMgRHcQ/featured',
    caption: 'Uomo Mondo',
  },
  {
    icon: 'mdi:web',
    link: 'https://www.google.com/url?q=https%3A%2F%2Fwww.liceogmarconifg.edu.it%2F&sa=D&sntz=1&usg=AOvVaw0xX2BPxy_oVDMjTVetbQ7D',
    caption: 'liceogmarconifg.edu.it',
  },
  {
    icon: 'mdi:youtube',
    link: 'https://www.youtube.com/watch?v=2_LH-xu_Uqo',
    caption: 'Liceo Marconi',
  },
]

const collapseContent = `Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, voluptatibus. 
  Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, voluptatibus. 
  Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, voluptatibus. 
  Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, voluptatibus.`

export default {
  components: {
    Hero,
    Section,
    Card,
    Avatar,
    Icon,
    CardText,
    InfiniteScrollHorizontal,
  },
  data() {
    return {
      imgUrl,
      professors,
      socials,
      collapseContent,
    }
  },
}
</script>
<style scoped></style>
