<script>
  import Header from "./components/Header.vue"
  import Navigation from "./components/Navigation.vue"
  import BookCard from "./components/BookCard.vue"
  import Footer from "./components/Footer.vue"

  export default {
    components: {
      Header,
      BookCard,
      Navigation,
      Footer,
    },
    data() {
      return {
        scrollColor: "",
        scrollThresholds: {
          320: [100, 1000, 1500, 2000, 2500, 3000, 3500, 4000],
          360: [100, 1000, 2000, 2500, 3500, 4000, 5000, 7000],
          393: [100, 1000, 2000, 3000, 3500, 4400, 5000, 7000],
          430: [100, 1000, 2000, 3000, 4000, 5000, 6000, 7000],
          768: [100, 1500, 2000, 3000, 4000, 5000, 6000, 7000],
          834: [100, 1500, 3000, 4500, 5500, 6500, 7500, 9000],
          884: [100, 1500, 3000, 4000, 5000, 6000, 7500, 9000],
          1114: [100, 800, 1600, 2400, 3200, 4000, 4500, 4800],
          1440: [100, 1000, 2000, 3000, 3900, 4699, 5499, 6499],
          1600: [100, 1000, 2000, 2500, 3500, 4000, 5000, 6000],
          1700: [100, 1000, 2000, 3000, 4000, 5000, 6000, 9000],
          1780: [100, 2000, 3000, 4000, 5500, 7000, 8000, 10000],
      },
        colorRanges: [
          { maxWidth: 320, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 360, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 393, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 430, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 768, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 834, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 884, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 1114, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 1440, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 1600, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 1700, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] },
          { maxWidth: 1780, colors: ["#F7E0A4", "#FF608C", "#FFF", "#00C1B5", "#FA6018", "#FFBE00", "#183ABE", "#E30611"] }
        ],
        bookDetails: [
          {
            image: 'https://backstagetalks.com/img/backstagetalks_cover_issue_8.png',
            alt: 'issue 8',
            issue: 8,
          },
          {
            image: 'https://backstagetalks.com/img/backstagetalks_cover_issue_7.png',
            alt: 'issue 7',
            issue: 7,
          },
          {
            image: 'https://backstagetalks.com/img/backstagetalks_cover_issue_6.png',
            alt: 'issue 6',
            issue: 6,
          },
          {
            image: 'https://backstagetalks.com/img/backstagetalks_cover_issue_5.png',
            alt: 'issue 5',
            issue: 5,
          },
          {
            image: 'https://backstagetalks.com/img/backstagetalks_cover_issue_4.png',
            alt: 'issue 4',
            issue: 4,
            sold: true,
          },
          {
            image: 'https://backstagetalks.com/img/backstagetalks_cover_issue_3.png',
            alt: 'issue 3',
            issue: 3,
            sold: true,
          },
          {
            image: 'https://backstagetalks.com/img/backstagetalks_cover2017.png',
            alt: 'issue 2',
            issue: 2,
          },
          {
            image: 'https://backstagetalks.com/img/backstagetalks_cover2016_n.png',
            alt: 'issue 1',
            issue: 1,
            sold: true,
          },
        ]
      }
    },

    mounted() {
      this.handleScrollEvent();
      window.addEventListener('scroll', this.handleScrollEvent);
    },

    beforeDestroy() {
      window.removeEventListener('scroll', this.handleScrollEvent);
    },
    methods: {
      handleScrollEvent() {
        let color = "";
        const scroll = window.scrollY;

        for (const range of this.colorRanges) {
          if (window.matchMedia(`(max-width: ${range.maxWidth}px)`).matches) {
            color = this.getColor(scroll, range.colors, this.scrollThresholds[range.maxWidth]);
            break;
          }
        }

        this.scrollColor = color;
        document.body.style.backgroundColor = this.scrollColor;
      },

      getColor(scroll, colors, thresholds) {
        for (let i = 0; i < thresholds.length; i++) {
          if (scroll < thresholds[i]) 
            return colors[i];
        }
        return colors[colors.length - 1];
      }
    }
  }
</script>

<template>
  <main class="m-5 xl:flex xl:justify-between">
    <Header />
    <div>
      <BookCard 
        v-for="book in bookDetails"
        :key="book.image"
        :image="book.image"
        :alt="book.alt"
        :issue="book.issue"
        :sold="book.sold"
      />
    </div>
    <Navigation />
    <Footer />
  </main>
</template>
