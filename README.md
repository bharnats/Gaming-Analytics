# pandas-Pymoli
Data Munging and Analysis of Purchase data for fantasy game "Heroes of Pymoli" using Pandas Library

{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "import pandas as pd\n",
    "import os\n",
    "import json"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Age</th>\n",
       "      <th>Gender</th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Item Name</th>\n",
       "      <th>Price</th>\n",
       "      <th>SN</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>38</td>\n",
       "      <td>Male</td>\n",
       "      <td>165</td>\n",
       "      <td>Bone Crushing Silver Skewer</td>\n",
       "      <td>3.37</td>\n",
       "      <td>Aelalis34</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>21</td>\n",
       "      <td>Male</td>\n",
       "      <td>119</td>\n",
       "      <td>Stormbringer, Dark Blade of Ending Misery</td>\n",
       "      <td>2.32</td>\n",
       "      <td>Eolo46</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>34</td>\n",
       "      <td>Male</td>\n",
       "      <td>174</td>\n",
       "      <td>Primitive Blade</td>\n",
       "      <td>2.46</td>\n",
       "      <td>Assastnya25</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>21</td>\n",
       "      <td>Male</td>\n",
       "      <td>92</td>\n",
       "      <td>Final Critic</td>\n",
       "      <td>1.36</td>\n",
       "      <td>Pheusrical25</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>23</td>\n",
       "      <td>Male</td>\n",
       "      <td>63</td>\n",
       "      <td>Stormfury Mace</td>\n",
       "      <td>1.27</td>\n",
       "      <td>Aela59</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Age Gender  Item ID                                  Item Name  Price  \\\n",
       "0   38   Male      165                Bone Crushing Silver Skewer   3.37   \n",
       "1   21   Male      119  Stormbringer, Dark Blade of Ending Misery   2.32   \n",
       "2   34   Male      174                            Primitive Blade   2.46   \n",
       "3   21   Male       92                               Final Critic   1.36   \n",
       "4   23   Male       63                             Stormfury Mace   1.27   \n",
       "\n",
       "             SN  \n",
       "0     Aelalis34  \n",
       "1        Eolo46  \n",
       "2   Assastnya25  \n",
       "3  Pheusrical25  \n",
       "4        Aela59  "
      ]
     },
     "execution_count": 4,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Read the JSON file into Pandas Dataframe\n",
    "file_path = os.path.join(\"purchase_data.json\")\n",
    "with open(file_path) as fileobj :\n",
    "    data = json.load(fileobj)\n",
    "purchase_df = pd.DataFrame(data)\n",
    "purchase_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "573\n"
     ]
    }
   ],
   "source": [
    "# Player count\n",
    "player_count =len(purchase_df[\"SN\"].value_counts())\n",
    "print(player_count)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "183\n"
     ]
    }
   ],
   "source": [
    "# Number Of Unique Items\n",
    "total_items = len(purchase_df[\"Item ID\"].value_counts())\n",
    "print(total_items)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "2.93\n"
     ]
    }
   ],
   "source": [
    "# Average Purchase Price\n",
    "avg_price = round(purchase_df[\"Price\"].mean(),2)\n",
    "print(avg_price)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "780"
      ]
     },
     "execution_count": 8,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Total number of purchases (number of rows in the data frame)\n",
    "len(purchase_df.index)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "2286.33\n"
     ]
    }
   ],
   "source": [
    "# Total Revenue\n",
    "total_revenue = round(purchase_df[\"Price\"].sum(),2)\n",
    "print(total_revenue)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "465\n"
     ]
    }
   ],
   "source": [
    "# Gender Demographics\n",
    "# Count of male players\n",
    "male_df = purchase_df.loc[purchase_df[\"Gender\"]==\"Male\",:]\n",
    "male_count = len(male_df[\"SN\"].unique())\n",
    "print(male_count)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "81.15\n"
     ]
    }
   ],
   "source": [
    "# Percentage of male players\n",
    "total_count = len(purchase_df[\"SN\"].unique())\n",
    "percent_male =round((male_count/total_count)*100,2)\n",
    "print(percent_male)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "100\n",
      "17.45\n"
     ]
    }
   ],
   "source": [
    "# female players count\n",
    "female_df = purchase_df.loc[purchase_df[\"Gender\"]==\"Female\",:]\n",
    "female_count = len(female_df[\"SN\"].unique())\n",
    "print(female_count)\n",
    "# Percentage of female players\n",
    "percent_female = round((female_count/total_count)*100, 2)\n",
    "print(percent_female)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "8\n",
      "1.4\n"
     ]
    }
   ],
   "source": [
    "# Percentage of other/undisclosed gender players\n",
    "other_count = total_count-male_count-female_count\n",
    "print(other_count)\n",
    "percent_other = round((other_count/total_count)*100,2)\n",
    "print(percent_other)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "633\n",
      "136\n"
     ]
    }
   ],
   "source": [
    "# purchase Analysis by gender\n",
    "# purchase count -male\n",
    "male_purchase = len(male_df)\n",
    "print(male_purchase)\n",
    "\n",
    "# purchase count -female\n",
    "female_purchase = len(female_df)\n",
    "print(female_purchase)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "2.95\n",
      "2.82\n"
     ]
    }
   ],
   "source": [
    "# Average Purchase Price\n",
    "# Male\n",
    "avg_price_male =round((male_df[\"Price\"].sum())/len(male_df[\"Price\"]),2)\n",
    "print(avg_price_male)\n",
    "# Female\n",
    "avg_price_female =round((female_df[\"Price\"].sum())/len(female_df[\"Price\"]),2)\n",
    "print(avg_price_female)\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "1867.68\n",
      "382.91\n"
     ]
    }
   ],
   "source": [
    "# Total Purchase Value\n",
    "# Total purchase Value- Male\n",
    "total_value_male = round(male_df[\"Price\"].sum(),2)\n",
    "print(total_value_male)\n",
    "# Total Purchase Value -Female\n",
    "total_value_female = round(female_df[\"Price\"].sum(),2)\n",
    "print(total_value_female)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "4.02\n",
      "4.02\n"
     ]
    }
   ],
   "source": [
    "# Normalised Totals\n",
    "# for male\n",
    "norm_total_val_male = round((total_value_male/male_count), 2)\n",
    "print(norm_total_val_male)\n",
    "# for female\n",
    "print(norm_total_val_male)\n",
    "norm_total_val_female = round((total_value_female/female_count), 2)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "45\n",
      "7\n"
     ]
    }
   ],
   "source": [
    "# Age demographics\n",
    "# find max and min of age column to fix the outer edge of the bins\n",
    "max_age = purchase_df[\"Age\"].max()\n",
    "min_age = purchase_df[\"Age\"].min()\n",
    "print(max_age)\n",
    "print(min_age)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Age</th>\n",
       "      <th>Gender</th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Item Name</th>\n",
       "      <th>Price</th>\n",
       "      <th>SN</th>\n",
       "      <th>Age Summary</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>38</td>\n",
       "      <td>Male</td>\n",
       "      <td>165</td>\n",
       "      <td>Bone Crushing Silver Skewer</td>\n",
       "      <td>3.37</td>\n",
       "      <td>Aelalis34</td>\n",
       "      <td>35 to 39</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>21</td>\n",
       "      <td>Male</td>\n",
       "      <td>119</td>\n",
       "      <td>Stormbringer, Dark Blade of Ending Misery</td>\n",
       "      <td>2.32</td>\n",
       "      <td>Eolo46</td>\n",
       "      <td>19 to 23</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>34</td>\n",
       "      <td>Male</td>\n",
       "      <td>174</td>\n",
       "      <td>Primitive Blade</td>\n",
       "      <td>2.46</td>\n",
       "      <td>Assastnya25</td>\n",
       "      <td>31 to 35</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>21</td>\n",
       "      <td>Male</td>\n",
       "      <td>92</td>\n",
       "      <td>Final Critic</td>\n",
       "      <td>1.36</td>\n",
       "      <td>Pheusrical25</td>\n",
       "      <td>19 to 23</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>23</td>\n",
       "      <td>Male</td>\n",
       "      <td>63</td>\n",
       "      <td>Stormfury Mace</td>\n",
       "      <td>1.27</td>\n",
       "      <td>Aela59</td>\n",
       "      <td>19 to 23</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Age Gender  Item ID                                  Item Name  Price  \\\n",
       "0   38   Male      165                Bone Crushing Silver Skewer   3.37   \n",
       "1   21   Male      119  Stormbringer, Dark Blade of Ending Misery   2.32   \n",
       "2   34   Male      174                            Primitive Blade   2.46   \n",
       "3   21   Male       92                               Final Critic   1.36   \n",
       "4   23   Male       63                             Stormfury Mace   1.27   \n",
       "\n",
       "             SN Age Summary  \n",
       "0     Aelalis34    35 to 39  \n",
       "1        Eolo46    19 to 23  \n",
       "2   Assastnya25    31 to 35  \n",
       "3  Pheusrical25    19 to 23  \n",
       "4        Aela59    19 to 23  "
      ]
     },
     "execution_count": 19,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# creating bins\n",
    "age_bins = [7,11,15,19,23,27,31,35,39,43,47]\n",
    "age_labels = [\"7 to 11\",\"11 to 15\",\"15 to 19\",\"19 to 23\",\"23 to 27\",\"27 to 31\",\"31 to 35\",\"35 to 39\",\"39 to 43\",\"43 to 47\"]\n",
    "purchase_df[\"Age Summary\"] = pd.cut(purchase_df[\"Age\"], age_bins, labels=age_labels)\n",
    "purchase_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 20,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Age Summary\n",
       "11 to 15     69\n",
       "15 to 19     86\n",
       "19 to 23    266\n",
       "23 to 27    169\n",
       "27 to 31     60\n",
       "31 to 35     42\n",
       "35 to 39     30\n",
       "39 to 43     16\n",
       "43 to 47      1\n",
       "7 to 11      22\n",
       "Name: Age, dtype: int64"
      ]
     },
     "execution_count": 20,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# purchase count by age bins\n",
    "age_groupby = purchase_df.groupby(\"Age Summary\")\n",
    "purchase_count_bins = age_groupby[\"Age\"].count()\n",
    "purchase_count_bins\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Age Summary\n",
       "11 to 15    2.86\n",
       "15 to 19    2.86\n",
       "19 to 23    2.88\n",
       "23 to 27    3.02\n",
       "27 to 31    2.96\n",
       "31 to 35    3.11\n",
       "35 to 39    2.75\n",
       "39 to 43    3.19\n",
       "43 to 47    2.72\n",
       "7 to 11     3.09\n",
       "Name: Price, dtype: float64"
      ]
     },
     "execution_count": 21,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Average Purchase Price within each bin\n",
    "avg_price_bin = round(age_groupby[\"Price\"].mean(),2)\n",
    "avg_price_bin"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Age Summary\n",
       "11 to 15    197.39\n",
       "15 to 19    246.06\n",
       "19 to 23    765.31\n",
       "23 to 27    510.02\n",
       "27 to 31    177.40\n",
       "31 to 35    130.64\n",
       "35 to 39     82.38\n",
       "39 to 43     51.03\n",
       "43 to 47      2.72\n",
       "7 to 11      67.91\n",
       "Name: Price, dtype: float64"
      ]
     },
     "execution_count": 22,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Total Purchase value\n",
    "tot_pur_value_bin = round(age_groupby[\"Price\"].sum(), 2)\n",
    "tot_pur_value_bin"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>SN</th>\n",
       "      <th>Amount_spent</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Adairialis76</td>\n",
       "      <td>2.46</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Aduephos78</td>\n",
       "      <td>6.70</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Aeduera68</td>\n",
       "      <td>5.80</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Aela49</td>\n",
       "      <td>2.46</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Aela59</td>\n",
       "      <td>1.27</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "             SN  Amount_spent\n",
       "0  Adairialis76          2.46\n",
       "1    Aduephos78          6.70\n",
       "2     Aeduera68          5.80\n",
       "3        Aela49          2.46\n",
       "4        Aela59          1.27"
      ]
     },
     "execution_count": 23,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Top 5 spenders\n",
    "SN_groupby = purchase_df.groupby(purchase_df[\"SN\"])\n",
    "SN_groupby_df = pd.DataFrame(SN_groupby[\"Price\"].sum())\n",
    "SN_groupby_df = SN_groupby_df.reset_index()\n",
    "SN_groupby_df.columns = [\"SN\",\"Amount_spent\"]\n",
    "#SN_groupby_df.sort_values(\"Amount_spent\",ascending=False).head()\n",
    "SN_groupby_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>SN</th>\n",
       "      <th>Purchase Count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Undirrala66</td>\n",
       "      <td>5</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Hailaphos89</td>\n",
       "      <td>4</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Sondastan54</td>\n",
       "      <td>4</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Mindimnya67</td>\n",
       "      <td>4</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Saedue76</td>\n",
       "      <td>4</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "            SN  Purchase Count\n",
       "0  Undirrala66               5\n",
       "1  Hailaphos89               4\n",
       "2  Sondastan54               4\n",
       "3  Mindimnya67               4\n",
       "4     Saedue76               4"
      ]
     },
     "execution_count": 24,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Purchase count for top 5 spenders\n",
    "pur_count_df = pd.DataFrame(purchase_df[\"SN\"].value_counts())\n",
    "pur_count_df = pur_count_df.reset_index()\n",
    "pur_count_df.columns=[\"SN\",\"Purchase Count\"]\n",
    "\n",
    "pur_count_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>SN</th>\n",
       "      <th>Amount_spent</th>\n",
       "      <th>Purchase Count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Adairialis76</td>\n",
       "      <td>2.46</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Aduephos78</td>\n",
       "      <td>6.70</td>\n",
       "      <td>3</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Aeduera68</td>\n",
       "      <td>5.80</td>\n",
       "      <td>3</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Aela49</td>\n",
       "      <td>2.46</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Aela59</td>\n",
       "      <td>1.27</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "             SN  Amount_spent  Purchase Count\n",
       "0  Adairialis76          2.46               1\n",
       "1    Aduephos78          6.70               3\n",
       "2     Aeduera68          5.80               3\n",
       "3        Aela49          2.46               1\n",
       "4        Aela59          1.27               1"
      ]
     },
     "execution_count": 25,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# merging the amount spent and purchase_count tables on SN\n",
    "merge1_df = pd.merge(SN_groupby_df,pur_count_df,on = \"SN\")\n",
    "merge1_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>SN</th>\n",
       "      <th>Avg Purchase price</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Adairialis76</td>\n",
       "      <td>2.46</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>Aduephos78</td>\n",
       "      <td>2.23</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Aeduera68</td>\n",
       "      <td>1.93</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Aela49</td>\n",
       "      <td>2.46</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>Aela59</td>\n",
       "      <td>1.27</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "             SN  Avg Purchase price\n",
       "0  Adairialis76                2.46\n",
       "1    Aduephos78                2.23\n",
       "2     Aeduera68                1.93\n",
       "3        Aela49                2.46\n",
       "4        Aela59                1.27"
      ]
     },
     "execution_count": 26,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "SN_groupby_avg_df = pd.DataFrame(round(SN_groupby[\"Price\"].mean(), 2))\n",
    "SN_groupby_avg_df = SN_groupby_avg_df.reset_index()\n",
    "SN_groupby_avg_df.columns = [\"SN\",\"Avg Purchase price\"]\n",
    "SN_groupby_avg_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 27,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>SN</th>\n",
       "      <th>Amount_spent</th>\n",
       "      <th>Purchase Count</th>\n",
       "      <th>Avg Purchase price</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>538</th>\n",
       "      <td>Undirrala66</td>\n",
       "      <td>17.06</td>\n",
       "      <td>5</td>\n",
       "      <td>3.41</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>428</th>\n",
       "      <td>Saedue76</td>\n",
       "      <td>13.56</td>\n",
       "      <td>4</td>\n",
       "      <td>3.39</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>354</th>\n",
       "      <td>Mindimnya67</td>\n",
       "      <td>12.74</td>\n",
       "      <td>4</td>\n",
       "      <td>3.18</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>181</th>\n",
       "      <td>Haellysu29</td>\n",
       "      <td>12.73</td>\n",
       "      <td>3</td>\n",
       "      <td>4.24</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>120</th>\n",
       "      <td>Eoda93</td>\n",
       "      <td>11.58</td>\n",
       "      <td>3</td>\n",
       "      <td>3.86</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "              SN  Amount_spent  Purchase Count  Avg Purchase price\n",
       "538  Undirrala66         17.06               5                3.41\n",
       "428     Saedue76         13.56               4                3.39\n",
       "354  Mindimnya67         12.74               4                3.18\n",
       "181   Haellysu29         12.73               3                4.24\n",
       "120       Eoda93         11.58               3                3.86"
      ]
     },
     "execution_count": 27,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# merging the amount spent and purchase_count tables and average purchase Price on SN\n",
    "top5_spenders_df = pd.merge(merge1_df,SN_groupby_avg_df,on = \"SN\")\n",
    "top5_spenders_df = top5_spenders_df.sort_values(\"Amount_spent\", ascending=False)\n",
    "\n",
    "top5_spenders_df = top5_spenders_df.iloc[0:5,:]\n",
    "top5_spenders_df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "top5_spenders_df.to_excel(\"Pymoli-Top 5 Spenders.xlsx\",index=False)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 29,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Amount_spent</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>0</td>\n",
       "      <td>1.82</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>9.12</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2</td>\n",
       "      <td>3.40</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>3</td>\n",
       "      <td>1.79</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>4</td>\n",
       "      <td>2.28</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Item ID  Amount_spent\n",
       "0        0          1.82\n",
       "1        1          9.12\n",
       "2        2          3.40\n",
       "3        3          1.79\n",
       "4        4          2.28"
      ]
     },
     "execution_count": 29,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# To evaluate 5 most popular items\n",
    "Item_groupby = purchase_df.groupby(purchase_df[\"Item ID\"])\n",
    "# Total purchase Value for each item\n",
    "Item_groupby_df = pd.DataFrame(Item_groupby[\"Price\"].sum())\n",
    "Item_groupby_df = Item_groupby_df.reset_index()\n",
    "Item_groupby_df.columns = [\"Item ID\",\"Amount_spent\"]\n",
    "Item_groupby_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 30,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Item Name</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>0</td>\n",
       "      <td>[Splinter]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>[Crucifer]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2</td>\n",
       "      <td>[Verdict]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>3</td>\n",
       "      <td>[Phantomlight]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>4</td>\n",
       "      <td>[Bloodlord's Fetish]</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Item ID             Item Name\n",
       "0        0            [Splinter]\n",
       "1        1            [Crucifer]\n",
       "2        2             [Verdict]\n",
       "3        3        [Phantomlight]\n",
       "4        4  [Bloodlord's Fetish]"
      ]
     },
     "execution_count": 30,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "Item_df = purchase_df.loc[:,[\"Item ID\",\"Item Name\"]]\n",
    "Item_name_groupby = Item_df.groupby(\"Item ID\")\n",
    "Item_name_groupby = Item_name_groupby[\"Item Name\"].unique()\n",
    "Item_name_df = pd.DataFrame(Item_name_groupby)\n",
    "Item_name_df = Item_name_df.reset_index()\n",
    "Item_name_df.columns = [\"Item ID\",\"Item Name\"]\n",
    "Item_name_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 31,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Amount_spent</th>\n",
       "      <th>Item Name</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>0</td>\n",
       "      <td>1.82</td>\n",
       "      <td>[Splinter]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>9.12</td>\n",
       "      <td>[Crucifer]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2</td>\n",
       "      <td>3.40</td>\n",
       "      <td>[Verdict]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>3</td>\n",
       "      <td>1.79</td>\n",
       "      <td>[Phantomlight]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>4</td>\n",
       "      <td>2.28</td>\n",
       "      <td>[Bloodlord's Fetish]</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Item ID  Amount_spent             Item Name\n",
       "0        0          1.82            [Splinter]\n",
       "1        1          9.12            [Crucifer]\n",
       "2        2          3.40             [Verdict]\n",
       "3        3          1.79        [Phantomlight]\n",
       "4        4          2.28  [Bloodlord's Fetish]"
      ]
     },
     "execution_count": 31,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "item_merge_df = pd.merge(Item_groupby_df,Item_name_df,on = \"Item ID\")\n",
    "item_merge_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Purchase Count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>84</td>\n",
       "      <td>11</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>39</td>\n",
       "      <td>11</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>31</td>\n",
       "      <td>9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>34</td>\n",
       "      <td>9</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>175</td>\n",
       "      <td>9</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Item ID  Purchase Count\n",
       "0       84              11\n",
       "1       39              11\n",
       "2       31               9\n",
       "3       34               9\n",
       "4      175               9"
      ]
     },
     "execution_count": 32,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Purchase Count for each Item ID\n",
    "Item_purchase_count_df = pd.DataFrame(purchase_df[\"Item ID\"].value_counts())\n",
    "Item_purchase_count_df = Item_purchase_count_df.reset_index()\n",
    "Item_purchase_count_df.columns = [\"Item ID\",\"Purchase Count\"]\n",
    "Item_purchase_count_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 33,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Amount_spent</th>\n",
       "      <th>Item Name</th>\n",
       "      <th>Purchase Count</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>0</td>\n",
       "      <td>1.82</td>\n",
       "      <td>[Splinter]</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>9.12</td>\n",
       "      <td>[Crucifer]</td>\n",
       "      <td>4</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2</td>\n",
       "      <td>3.40</td>\n",
       "      <td>[Verdict]</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>3</td>\n",
       "      <td>1.79</td>\n",
       "      <td>[Phantomlight]</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>4</td>\n",
       "      <td>2.28</td>\n",
       "      <td>[Bloodlord's Fetish]</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Item ID  Amount_spent             Item Name  Purchase Count\n",
       "0        0          1.82            [Splinter]               1\n",
       "1        1          9.12            [Crucifer]               4\n",
       "2        2          3.40             [Verdict]               1\n",
       "3        3          1.79        [Phantomlight]               1\n",
       "4        4          2.28  [Bloodlord's Fetish]               1"
      ]
     },
     "execution_count": 33,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "merge2_df = pd.merge(item_merge_df,Item_purchase_count_df,on = \"Item ID\")\n",
    "merge2_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 34,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Item Price</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>0</td>\n",
       "      <td>[1.82]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>[2.28]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2</td>\n",
       "      <td>[3.4]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>3</td>\n",
       "      <td>[1.79]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>4</td>\n",
       "      <td>[2.28]</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Item ID Item Price\n",
       "0        0     [1.82]\n",
       "1        1     [2.28]\n",
       "2        2      [3.4]\n",
       "3        3     [1.79]\n",
       "4        4     [2.28]"
      ]
     },
     "execution_count": 34,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Item Price dataframe\n",
    "price_df = purchase_df.loc[:,[\"Item ID\",\"Price\"]]\n",
    "Item_price_groupby = price_df.groupby(\"Item ID\")\n",
    "Item_price_groupby = Item_price_groupby[\"Price\"].unique()\n",
    "Item_price_df = pd.DataFrame(Item_price_groupby)\n",
    "Item_price_df = Item_price_df.reset_index()\n",
    "Item_price_df.columns = [\"Item ID\",\"Item Price\"]\n",
    "Item_price_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 35,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Amount_spent</th>\n",
       "      <th>Item Name</th>\n",
       "      <th>Purchase Count</th>\n",
       "      <th>Item Price</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>0</td>\n",
       "      <td>1.82</td>\n",
       "      <td>[Splinter]</td>\n",
       "      <td>1</td>\n",
       "      <td>[1.82]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>9.12</td>\n",
       "      <td>[Crucifer]</td>\n",
       "      <td>4</td>\n",
       "      <td>[2.28]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>2</td>\n",
       "      <td>3.40</td>\n",
       "      <td>[Verdict]</td>\n",
       "      <td>1</td>\n",
       "      <td>[3.4]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>3</td>\n",
       "      <td>1.79</td>\n",
       "      <td>[Phantomlight]</td>\n",
       "      <td>1</td>\n",
       "      <td>[1.79]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>4</td>\n",
       "      <td>2.28</td>\n",
       "      <td>[Bloodlord's Fetish]</td>\n",
       "      <td>1</td>\n",
       "      <td>[2.28]</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Item ID  Amount_spent             Item Name  Purchase Count Item Price\n",
       "0        0          1.82            [Splinter]               1     [1.82]\n",
       "1        1          9.12            [Crucifer]               4     [2.28]\n",
       "2        2          3.40             [Verdict]               1      [3.4]\n",
       "3        3          1.79        [Phantomlight]               1     [1.79]\n",
       "4        4          2.28  [Bloodlord's Fetish]               1     [2.28]"
      ]
     },
     "execution_count": 35,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# merge to create the final dataframe based on Item ID\n",
    "item_id_df = pd.merge(merge2_df,Item_price_df,on = \"Item ID\")\n",
    "item_id_df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 36,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Amount_spent</th>\n",
       "      <th>Item Name</th>\n",
       "      <th>Purchase Count</th>\n",
       "      <th>Item Price</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>39</th>\n",
       "      <td>39</td>\n",
       "      <td>25.85</td>\n",
       "      <td>[Betrayal, Whisper of Grieving Widows]</td>\n",
       "      <td>11</td>\n",
       "      <td>[2.35]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>84</th>\n",
       "      <td>84</td>\n",
       "      <td>24.53</td>\n",
       "      <td>[Arcane Gem]</td>\n",
       "      <td>11</td>\n",
       "      <td>[2.23]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>31</th>\n",
       "      <td>31</td>\n",
       "      <td>18.63</td>\n",
       "      <td>[Trickster]</td>\n",
       "      <td>9</td>\n",
       "      <td>[2.07]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>174</th>\n",
       "      <td>175</td>\n",
       "      <td>11.16</td>\n",
       "      <td>[Woeful Adamantite Claymore]</td>\n",
       "      <td>9</td>\n",
       "      <td>[1.24]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>13</th>\n",
       "      <td>13</td>\n",
       "      <td>13.41</td>\n",
       "      <td>[Serenity]</td>\n",
       "      <td>9</td>\n",
       "      <td>[1.49]</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "     Item ID  Amount_spent                               Item Name  \\\n",
       "39        39         25.85  [Betrayal, Whisper of Grieving Widows]   \n",
       "84        84         24.53                            [Arcane Gem]   \n",
       "31        31         18.63                             [Trickster]   \n",
       "174      175         11.16            [Woeful Adamantite Claymore]   \n",
       "13        13         13.41                              [Serenity]   \n",
       "\n",
       "     Purchase Count Item Price  \n",
       "39               11     [2.35]  \n",
       "84               11     [2.23]  \n",
       "31                9     [2.07]  \n",
       "174               9     [1.24]  \n",
       "13                9     [1.49]  "
      ]
     },
     "execution_count": 36,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# top 5 popular items based on purchase count\n",
    "most_popular_items_df = item_id_df.sort_values(\"Purchase Count\",ascending=False)\n",
    "most_popular_items_df= most_popular_items_df.iloc[0:5,:]\n",
    "most_popular_items_df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 37,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "# Export the results to Excel sheet\n",
    "most_popular_items_df.to_excel(\"Pymoli-Popular 5 Items.xlsx\",index=False)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 38,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style>\n",
       "    .dataframe thead tr:only-child th {\n",
       "        text-align: right;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: left;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Item ID</th>\n",
       "      <th>Amount_spent</th>\n",
       "      <th>Item Name</th>\n",
       "      <th>Purchase Count</th>\n",
       "      <th>Item Price</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>34</th>\n",
       "      <td>34</td>\n",
       "      <td>37.26</td>\n",
       "      <td>[Retribution Axe]</td>\n",
       "      <td>9</td>\n",
       "      <td>[4.14]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>115</th>\n",
       "      <td>115</td>\n",
       "      <td>29.75</td>\n",
       "      <td>[Spectral Diamond Doomblade]</td>\n",
       "      <td>7</td>\n",
       "      <td>[4.25]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>32</th>\n",
       "      <td>32</td>\n",
       "      <td>29.70</td>\n",
       "      <td>[Orenmir]</td>\n",
       "      <td>6</td>\n",
       "      <td>[4.95]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>103</th>\n",
       "      <td>103</td>\n",
       "      <td>29.22</td>\n",
       "      <td>[Singed Scalpel]</td>\n",
       "      <td>6</td>\n",
       "      <td>[4.87]</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>107</th>\n",
       "      <td>107</td>\n",
       "      <td>28.88</td>\n",
       "      <td>[Splitter, Foe Of Subtlety]</td>\n",
       "      <td>8</td>\n",
       "      <td>[3.61]</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "     Item ID  Amount_spent                     Item Name  Purchase Count  \\\n",
       "34        34         37.26             [Retribution Axe]               9   \n",
       "115      115         29.75  [Spectral Diamond Doomblade]               7   \n",
       "32        32         29.70                     [Orenmir]               6   \n",
       "103      103         29.22              [Singed Scalpel]               6   \n",
       "107      107         28.88   [Splitter, Foe Of Subtlety]               8   \n",
       "\n",
       "    Item Price  \n",
       "34      [4.14]  \n",
       "115     [4.25]  \n",
       "32      [4.95]  \n",
       "103     [4.87]  \n",
       "107     [3.61]  "
      ]
     },
     "execution_count": 38,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Most Profitable Items\n",
    "# sorting the above table based on the Amount_spent\n",
    "most_profitable_items_df = item_id_df.sort_values(\"Amount_spent\",ascending=False)\n",
    "most_profitable_items_df=most_profitable_items_df.iloc[0:5,:]\n",
    "most_profitable_items_df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 39,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": [
    "most_profitable_items_df.to_excel(\"Pymoli-Most Profitable Items.xlsx\",index=False)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.1"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
