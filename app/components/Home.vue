<template>
    <Page>
        <ActionBar title="Count BIZ" />

        <StackLayout>
            <BottomNavigation>
                <TabStrip>
                    <TabStripItem>
                        <Label text="Home"></Label>
                        <Image src="res://home"></Image>
                    </TabStripItem>
                    <TabStripItem>
                        <Label text="Overview"></Label>
                        <Image src="res://settings"></Image>
                    </TabStripItem>
                    <TabStripItem>
                        <Label text="Account"></Label>
                        <Image src="res://favorites"></Image>
                    </TabStripItem>
                    <TabStripItem>
                        <Label text="report"></Label>
                        <Image src="res://browse"></Image>
                    </TabStripItem>
                </TabStrip>
                <TabContentItem>
                    <ListView for="story in storys" @itemTap="onItemTap">
                        <v-template>
                            <StackLayout height="350">
                                <Image :src="story.img" height="300"
                                    stretch="aspectFill" />
                                <Label :text="story.name" class="h2" />
                                <Label :text="story.content" class="h3" />
                            </StackLayout>
                        </v-template>
                    </ListView>
                </TabContentItem>
                <TabContentItem>
                    <GridLayout>
                        <ScrollView>
                            <StackLayout orientation="vertical">
                                <Image
                                    src="https://i.loli.net/2021/11/28/m4r9PgIlnaO1jtD.png" />
                                <Label class="m-10 m-y-20 h2"
                                    text="Overview" />
                                <FlexboxLayout class="m-x-10 m-b-30 h2"
                                    height="120" flexWrap="wrap">
                                    <Label text="ASSET: 26,681.00"
                                        class='text-center p-x-20'
                                        backgroundColor="#FFFFFF"
                                        color="#FF4500" flexGrow="6" />
                                    <Label text="LIABILITY: 16,000.00"
                                        class='text-center'
                                        backgroundColor="#F5F5F5"
                                        color="#32CD32" flexGrow="6" />
                                    <Label text="NET ASSETS: 10,681.00"
                                        class='text-center'
                                        backgroundColor="#DCDCDC"
                                        color="#696969" flexGrow="6" />
                                </FlexboxLayout>
                                <Label class="m-x-10 m-t-20 h2"
                                    text="Nov. 2021 Financial Presentation" />
                                <TextView editable="false">
                                    <FormattedString class="h3">
                                        <Span text=" Today is your " />
                                        <Span text="24th" fontWeight="Bold" />
                                        <Span
                                            text=" day of bookkeeping, with a total of" />
                                        <Span text=" 59 " fontWeight="Bold" />
                                        <Span text="entries in this book." />
                                        <Span
                                            text=" The budget for this month is" />
                                        <Span text=" $12,000.00 "
                                            color="#32CD32"
                                            fontWeight="Bold" />
                                        <Span text="and" />
                                        <Span text=" $9,319.00 "
                                            color="#FF4500"
                                            fontWeight="Bold" />
                                        <Span text="has been used, leaving" />
                                        <Span text=" $2,681.00 "
                                            fontWeight="Bold" />
                                        <Span text="available." />
                                    </FormattedString>
                                </TextView>
                                <Label class="m-x-10 h2"
                                    text="Major expense charts" />
                                <GridLayout class="m-x-10" rows="*"
                                    height="1000px">
                                    <RadPieChart allowAnimation=" true"
                                        row="0">
                                        <PieSeries v-tkPieSeries
                                            selectionMode="DataPoint"
                                            expandRadius="0.4"
                                            outerRadiusFactor="0.7"
                                            :items="pieSource"
                                            valueProperty="amount"
                                            legendLabel="brand" />
                                        <RadLegendView v-tkPieLegend
                                            position="Right"
                                            title="Expenses chart"
                                            offsetOrigin="TopRight"
                                            width="100"
                                            enableSelection="true" />
                                    </RadPieChart>
                                </GridLayout>
                                <GridLayout class="m-x-10" rows="*"
                                    height="600px">
                                    <RadCartesianChart row="0"
                                        style="font-size: 12;">
                                        <LineSeries v-tkCartesianSeries
                                            :items="categoricalSource"
                                            categoryProperty="month"
                                            valueProperty="amount" />
                                        <CategoricalAxis
                                            v-tkCartesianHorizontalAxis />
                                        <LinearAxis
                                            v-tkCartesianVerticalAxis />
                                    </RadCartesianChart>
                                </GridLayout>
                            </StackLayout>
                        </ScrollView>
                    </GridLayout>
                </TabContentItem>
                <TabContentItem>
                    <GridLayout>
                        <ScrollView>
                            <StackLayout class="home-panel">
                                <Image
                                    src="https://images.pexels.com/photos/6266283/pexels-photo-6266283.jpeg?auto=compress&cs=tinysrgb&dpr=2&w=500" />
                                <Label class="m-t-20 h1 text-center"
                                    text="Cash Account" />
                                <FlexboxLayout flexDirection="row-reverse"
                                    class="m-30 h2" height="240"
                                    flexWrap="wrap">

                                    <Label text="Balance: 9,796.00"
                                        backgroundColor="#FFFFE0"
                                        color="#7B68EE" flexGrow="4" />
                                    <Label text="Cash in: 39,865.00"
                                        backgroundColor="#FAFAD2"
                                        color="#A52A2A" flexGrow="5" />
                                    <Label text="Cash expenditure: 30,068.00"
                                        backgroundColor="#EEE8AA"
                                        color="#3CB371" flexGrow="6" />
                                </FlexboxLayout>

                                <GridLayout rows="*" height="1000px">
                                    <RadPieChart allowAnimation="true"
                                        row="0">
                                        <DonutSeries v-tkPieSeries
                                            selectionMode="DataPoint"
                                            expandRadius="0.4"
                                            outerRadiusFactor="0.7"
                                            innerRadiusFactor="0.4"
                                            :items="pieSourceXM"
                                            valueProperty="Amount"
                                            legendLabel="Brand" />
                                        <RadLegendView v-tkPieLegend
                                            position="Right"
                                            title="Cash Account"
                                            offsetOrigin="TopRight"
                                            width="110"
                                            enableSelection="true" />
                                    </RadPieChart>
                                </GridLayout>

                                <GridLayout rows="*" height="1000px">
                                    <RadCartesianChart row="0"
                                        style="font-size: 12;">
                                        <LineSeries v-tkCartesianSeries
                                            :items="categoricalSourceXM"
                                            categoryProperty="Country"
                                            valueProperty="Amount" />
                                        <CategoricalAxis
                                            v-tkCartesianHorizontalAxis />
                                        <LinearAxis
                                            v-tkCartesianVerticalAxis />
                                    </RadCartesianChart>
                                </GridLayout>
                            </StackLayout>
                        </ScrollView>
                    </GridLayout>
                </TabContentItem>
                <TabContentItem>
                    <ScrollView>
                        <StackLayout class="home-panel">
                            <!--Add your page content here-->
                            <GridLayout rows="auto, *" height="1000px">
                                <Label row="0"
                                    text="Comparative Expenditure Statement"
                                    class='m-20' textWrap="true" />
                                <RadCartesianChart row="1"
                                    selectionMode="Single"
                                    style="font-size: 12;">
                                    <CategoricalAxis lineColor="#b0b0b0"
                                        lineThickness="1"
                                        v-tkCartesianHorizontalAxis />
                                    <LinearAxis lineColor="#b0b0b0"
                                        lineThickness="1"
                                        v-tkCartesianVerticalAxis />
                                    <AreaSeries seriesName="Area"
                                        categoryProperty="category"
                                        :items="areaSource" stackMode="Stack"
                                        valueProperty="amount"
                                        selectionMode="Series"
                                        v-tkCartesianSeries />
                                    <AreaSeries seriesName="Area"
                                        categoryProperty="category"
                                        :items="areaSource2" stackMode="Stack"
                                        valueProperty="amount"
                                        selectionMode="Series"
                                        v-tkCartesianSeries />
                                    <RadCartesianChartGrid
                                        horizontalLinesVisible="true"
                                        verticalLinesVisible="false"
                                        verticalStripLinesVisible="false"
                                        horizontalStripLinesVisible="false"
                                        horizontalStrokeColor="#e5e5e5"
                                        v-tkCartesianGrid />
                                    <Palette seriesName="Area"
                                        v-tkCartesianPalette>
                                        <PaletteEntry fillColor="#b2efe6"
                                            strokeColor="#08caab"
                                            strokeWidth="2" />
                                        <PaletteEntry fillColor="#b2d2d1"
                                            strokeColor="#026968"
                                            strokeWidth="2" />
                                    </Palette>
                                    <Palette seriesName="Area"
                                        seriesState="Selected"
                                        v-tkCartesianPalette>
                                        <PaletteEntry fillColor="#b2efe6"
                                            strokeColor="#026555"
                                            strokeWidth="2" />
                                        <PaletteEntry fillColor="#b2d2d1"
                                            strokeColor="#003434"
                                            strokeWidth="2" />
                                    </Palette>
                                </RadCartesianChart>
                            </GridLayout>
                            <Label textWrap="true" text="Data Summary"
                                class="h1 description-label m-x-20" />
                            <Label textWrap="true"
                                text="Due to the impact of covid-19, all expenditures are significantly reduced in 2020 compared to 2021, especially the consumption demand for cloths and entertainment is significantly reduced."
                                class="h3 description-label m-x-20" />

                            <!--hjf-->
                            <Label row="0"
                                text="Actual Expenditure in 2020"
                                class='m-20' textWrap="true" />
                            <GridLayout rows="*" height="1000px">
                                <RadCartesianChart row="0"
                                    style="font-size: 12;">
                                    <BarSeries v-tkCartesianSeries
                                        :items="dataSourceBudget"
                                        categoryProperty="category"
                                        valueProperty="amount" />
                                    <CategoricalAxis
                                        v-tkCartesianHorizontalAxis />
                                    <LinearAxis v-tkCartesianVerticalAxis />
                                </RadCartesianChart>
                            </GridLayout>
                            <Label textWrap="true" text="Data Summary"
                                class="h1 description-label m-x-20" />
                            <Label textWrap="true"
                                text="The item of Shopping for Expenditure has the highest amount with 82,000. And the second highest is the item of travelling with 50,000."
                                class="h3 description-label m-x-20" />

                            <!--xm-->
                            <Label class="m-t-20 h1 text-center"
                                text="Balance Sheet" color="#1E90FF" />

                            <Label class="m-t-20 h2 text-center"
                                text="Asset Pie Chart" color="#CD5C5C" />

                            <GridLayout rows="*" height="1000px">
                                <RadPieChart allowAnimation="true" row="0">
                                    <PieSeries v-tkPieSeries
                                        selectionMode="DataPoint"
                                        expandRadius="0.4"
                                        outerRadiusFactor="0.7"
                                        :items="pieSourceXM1"
                                        valueProperty="Amount"
                                        legendLabel="Asset" />
                                    <RadLegendView v-tkPieLegend
                                        position="Right"
                                        title="Asset Pie Chart"
                                        offsetOrigin="TopRight" width="110"
                                        enableSelection="true" />
                                </RadPieChart>
                            </GridLayout>

                            <Label class="m-t-20 h2 text-center"
                                text="Liability Pie Chart" color="#3CB371" />

                            <GridLayout rows="*" height="1000px">
                                <RadPieChart allowAnimation="true" row="0">
                                    <PieSeries v-tkPieSeries
                                        selectionMode="DataPoint"
                                        expandRadius="0.4"
                                        outerRadiusFactor="0.7"
                                        :items="pieSourceXM2"
                                        valueProperty="Amount"
                                        legendLabel="Liability" />
                                    <RadLegendView v-tkPieLegend
                                        position="Right"
                                        title="Liability Pie Chart"
                                        offsetOrigin="TopRight" width="110"
                                        enableSelection="true" />
                                </RadPieChart>
                            </GridLayout>
                        </StackLayout>
                    </ScrollView>
                </TabContentItem>
            </BottomNavigation>
        </StackLayout>
    </Page>
</template>

<script>
    import Vue from "nativescript-vue";
    import RadCartesianChart from "nativescript-ui-chart/vue";
    Vue.use(RadCartesianChart);

    export default {
        methods: {
            onItemTap: function(args) {
                console.log("Item with index: " + args.index + " tapped");
                // this.$navigateTo(Person, {
                //     transition: {},
                //     props: {
                //         id: args.index
                //     }
                // });
            },
            fetchStorys: async function() {
                const response = await fetch(
                    "https://api.npoint.io/b4f1074335be20031e4c"
                );
                if (response.ok) {
                    this.storys = await response.json();
                    // console.log(JSON.stringify(this.storys));
                } else {
                    console.log(response.statusText);
                }
            },
            fetchMajorExpense: async function() {
                const response = await fetch(
                    "https://api.npoint.io/bd0c8c7e3ea9046e5a9d"
                );
                const labels = [
                    "Property",
                    "Learning",
                    "Interests",
                    "Food",
                    "Leisure",
                    "Shopping",
                    "Clothing",
                    "Medical care",
                    "Communication",
                    "Transportation"
                ];
                const data = await response.json();
                this.pieSource = data.map((item, i) => {
                    return {
                        brand: labels[i],
                        amount: item
                    };
                });
            },
            fetchExpenditureTrend: async function() {
                const response = await fetch(
                    "https://api.npoint.io/83605d43e35b3d604bfc"
                );
                const labels = [
                    "Jan",
                    "Feb",
                    "Mar",
                    "Apr",
                    "May",
                    "June",
                    "July",
                    "Aug",
                    "Sep",
                    "Oct",
                    "Nov"
                ];
                const data = await response.json();
                this.categoricalSource = data.map((item, i) => {
                    return {
                        month: labels[i],
                        amount: item
                    };
                });
            },
            fetchAreaChart: async function() {
                const response = await fetch(
                    "https://api.npoint.io/57a102de728474181f83"
                );
                const labels = [
                    "Clothes",
                    "Food",
                    "Communication",
                    "Leisure",
                    "Medical care"
                ];
                const data = await response.json();
                this.areaSource = data[0].map((item, i) => {
                    return {
                        category: labels[i],
                        amount: item
                    };
                });
                this.areaSource2 = data[1].map((item, i) => {
                    return {
                        category: labels[i],
                        amount: item
                    };
                });
            },
            fetchBudget: async function() {
                const response = await fetch(
                    "https://api.npoint.io/2305c1ad735fe07a28a4"
                );
                const labels = [
                    "Shopping",
                    "Traffic",
                    "Telephone",
                    "Study",
                    "Health Care",
                    "Travelling"
                ];
                const data = await response.json();
                this.dataSourceBudget = data[1].map((item, i) => {
                    return {
                        category: labels[i],
                        amount: item
                    };
                });
            }
        },
        data() {
            return {
                gaugeValue: 2,
                storys: [],
                categoricalSource: [],
                pieSource: [],
                areaSource: [0],
                areaSource2: [1],
                dataSourceBudget: [],
                pieSourceXM: [{
                        Brand: "Balance",
                        Amount: 9796
                    },
                    {
                        Brand: "Cash in",
                        Amount: 39865
                    },
                    {
                        Brand: "Cash expenditure",
                        Amount: 30069
                    }
                ],
                categoricalSourceXM: [{
                        Country: "Balance",
                        Amount: 9796,
                        SecondVal: 14,
                        ThirdVal: 24
                    },
                    {
                        Country: "Cash in",
                        Amount: 39865,
                        SecondVal: 23,
                        ThirdVal: 25
                    },
                    {
                        Country: "Cash expenditure",
                        Amount: 30069,
                        SecondVal: 17,
                        ThirdVal: 23
                    }
                ],
                pieSourceXM1: [{
                        Asset: "Cash",
                        Amount: 5300
                    },
                    {
                        Asset: "Bank Cards",
                        Amount: 18000
                    },
                    {
                        Asset: "Deposit Book",
                        Amount: 31000
                    },
                    {
                        Asset: "Alipay",
                        Amount: 3000
                    },
                    {
                        Asset: "Wechat Wallet",
                        Amount: 2500
                    },
                    {
                        Asset: "Octpus",
                        Amount: 899
                    },
                    {
                        Asset: "Stock Accounts",
                        Amount: 25000
                    }
                ],
                pieSourceXM2: [{
                        Liability: "Accounts Payable",
                        Amount: 5300
                    },
                    {
                        Liability: "Short-term Loans",
                        Amount: 3500
                    },
                    {
                        Liability: "Long-term Loans",
                        Amount: 8000
                    },
                    {
                        Liability: "Bills Payable",
                        Amount: 2400
                    },
                    {
                        Liability: "Taxes Payable",
                        Amount: 1500
                    }
                ]
            };
        },

        async mounted() {
            await this.fetchStorys();
            await this.fetchMajorExpense();
            await this.fetchExpenditureTrend();
            await this.fetchAreaChart();
            await this.fetchBudget();
        }
    };
</script>

<style scoped>
    .home-panel {
        vertical-align: center;
        font-size: 20;
        margin: 15;
    }

    .description-label {
        margin-bottom: 15;
    }
</style>