<template>
  <q-page class="relative-position">
    <q-scroll-area class="absolute fullscreen">
      <div class="q-py-lg q-px-md row items-end q-col-gutter-md">
        <div class="col">
          <q-input
            bottom-slots
            v-model="newQweetContent"
            class="new-qweet"
            placeholder="What's happening?"
            counter
            maxlength="280"
            autogrow
          >
            <template v-slot:before>
              <q-avatar size="xl">
                <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
              </q-avatar>
            </template>
          </q-input>
        </div>
        <div class="col col-shrink">
          <q-btn
            @click="addNewQweet"
            :disable="!newQweetContent"
            class="q-mb-lg"
            unelevated
            rounded
            color="primary"
            label="Qweet"
          />
        </div>
      </div>
      <q-separator class="divider" size="10px" color="grey-2" />
      <q-list seperator>
        <transition-group
          appear
          enter-active-class="animated fadeIn slower"
          leave-active-class="animated fadeOut slower"
        >
          <q-item
            v-for="qweet in qweets"
            :key="qweet.date"
            class="qweet q-py-md"
          >
            <q-item-section avatar top>
              <q-avatar>
                <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
              </q-avatar>
            </q-item-section>

            <q-item-section>
              <q-item-label class="text-subtitle1"
                ><strong>Chloe</strong></q-item-label
              >
              <span class="text-grey-7"
                >@Chloe__chlo <br class="lt-md" />&bull;
                {{ relativeDate(qweet.date) }}</span
              >
              <q-item-label class="qweet-content text-body1"
                >{{ qweet.content }}
              </q-item-label>
              <div class="qweet-icons row justify-between q-mt-sm">
                <q-btn
                  flat
                  round
                  color="grey"
                  size="sm"
                  icon="far fa-comment"
                />
                <q-btn
                  flat
                  round
                  color="grey"
                  size="sm"
                  icon="fas fa-retweet"
                />
                <q-btn flat round color="grey" size="sm" icon="far fa-heart" />
                <q-btn
                  @click="deleteQweet(qweet)"
                  flat
                  round
                  color="grey"
                  size="sm"
                  icon="fas fa-trash"
                />
              </div>
            </q-item-section>
          </q-item>
        </transition-group>
      </q-list>
    </q-scroll-area>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import { formatDistance } from "date-fns";
export default defineComponent({
  name: "PageHome",
  data() {
    return {
      newQweetContent: "",
      qweets: [
        {
          content: "Sometimes you gotta run before you can walk",
          date: 1700837249165,
        },
        {
          content:
            "Lorem ipsum dolor sit, amet consectetur adipisicing elit.Accusantium obcaecati atque id, dolor natus, sequi accusamus nihil deserunt quo rerum, sint suscipit fuga rem officia enim corporis.Quis, eius eligendi.",
          date: 1700837249166,
        },
      ],
    };
  },
  methods: {
    relativeDate(value) {
      return formatDistance(value, new Date());
    },
    addNewQweet() {
      let newQweet = {
        content: this.newQweetContent,
        date: Date.now(),
      };
      this.qweets.unshift(newQweet);
      this.newQweetContent = "";
    },
    deleteQweet(qweet) {
      let dateToDelete = qweet.date;
      let index = this.qweets.findIndex((qweet) => qweet.date === dateToDelete);
      console.log(index);
      this.qweets.splice(index, 1);
    },
  },
});
</script>
<style lang="sass">
.new-qweet
  textarea
  font-size:19px
  line-height:1.4 !important

.divider
  border-top:1px
  border-button:1px
  border-color:$grey-4

.qweet-component
  white-space:pre-line

.qweet-icons
  margin-left:-5px

.qweet:not(first-child)
  border-top: 1px
  rgba:(0,0,0,0.12)
</style>
