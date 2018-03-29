<template>
  <div id="root">
    <div id="media" v-for="submission in sortSubmission" :class="{ 'blue-border': submission.votes>=20  }" :key="submission.id">
        <div class="put">
            <figure>
                <img class="image is-64x64" :src="submission.submissionImage">
            </figure>
            <div class="media-content">
                <div class="content">
                    <p>
                        <strong>
                            <a :href="submission.url">
                                {{submission.title}}
                            </a>
                            <span class="tag is-small">
                                #{{submission.id}}
                            </span>
                        </strong>
                        <br>
                        {{submission.description}}
                        <br>
                        <small class="is-size-7">
                            Submitted by:
                            <img :src="submission.avatar" class="image is-24x24">
                        </small>
                    </p>
                </div>
            </div>
            <div class="media-right">
                <span class="icon is-small" @click="upvote(submission.id)">
                    <i class="fa fa-chevron-up"></i>
                    <strong class="has-text-info">{{submission.votes}}</strong>
                </span>
            </div>
        </div>
      </div>
   </div>
</template>
<script>
export default {
  data() {
    return {
      submissions: [
        {
          id: 1,
          title: "Yellow Pail",
          description: "On-demand sand castle construction expertise.",
          url: "#",
          votes: 16,
          avatar: require("../assets/img/avatars/daniel.jpg"),
          submissionImage: require("../assets/img/submissions/image-yellow.png")
        },
        {
          id: 2,
          title: "Supermajority: The Fantasy Congress League",
          description:
            "Earn points when your favorite politicians pass legislation.",
          url: "#",
          votes: 11,
          avatar: require("../assets/img/avatars/kristy.png"),
          submissionImage: require("../assets/img/submissions/image-rose.png")
        },
        {
          id: 3,
          title: "Tinfoild: Tailored tinfoil hats",
          description: "We have your measurements and shipping address.",
          url: "#",
          votes: 17,
          avatar: require("../assets/img/avatars/veronika.jpg"),
          submissionImage: require("../assets/img/submissions/image-steel.png")
        },
        {
          id: 4,
          title: "Haught or Naught",
          description: "High-minded or absent-minded? You decide.",
          url: "#",
          votes: 9,
          avatar: require("../assets/img/avatars/molly.png"),
          submissionImage: require("../assets/img/submissions/image-aqua.png")
        }
      ]
    };
  },
  methods:{
      upvote(submissionId){
          const submission=this.submissions.find(
              submission=>submission.id===submissionId
          );
          submission.votes++;
      }
  },
  computed:{
      sortSubmission () {
          return this.submissions.sort((a,b)=>{
              return b.votes-a.votes;
          })
      }
  }
};
</script>

<style scoped>
#media {
  max-width: 600px;
  margin: 0 auto;
  border: 1px solid #e6e7e9;
  padding: 1em 1.5em 0.5em 1.5em;
  border-radius: 0.3em;
}
.put {
  display: flex;
  width: 100%;
}
.tag {
  font-size: 0.6rem !important;
}
.image.is-24x24 {
  display: inline;
  position: relative;
  top: 5px;
  border-radius: 20px;
}

#media + #media {
    margin-top: 1.5rem;
}

.media-content {
  margin-left: 15px;
}
.icon {
  cursor: pointer;
}
i {
  margin-top: -3px;
}
.blue-border{
    border:1px solid #3373dc !important
}
</style>
