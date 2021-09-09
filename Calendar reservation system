/*
// Sample code to perform I/O:

#include <iostream>

using namespace std;

int main() {
	int num;
	cin >> num;										// Reading input from STDIN
	cout << "Input number is " << num << endl;		// Writing output to STDOUT
}

// Warning: Printing unwanted or ill-formatted data to output will cause the test cases to fail
*/

// Write your code here
#include <iostream>
#include <bits/stdc++.h>
#include <string>
#include <vector> 

using namespace std;

class evnt
{
	public:
	int eveid;
	string day;
	int start;
	int end;
	vector <evnt*> parts;


};

class user
{
	public:
	string name;
	int id;
	vector<int> dates;
	vector < vector < pair <int,int> > > calendar;
	vector < vector <evnt*>> parting;
};

int numusers = 0;
int numevents = 0;

vector<user*> users;
vector<string> usernames;

// vector<evnt*> evnts;

void adduser(string username)
{
	user* user1 = new user;
	user1->id = numusers;
	numusers++;
	if( find(usernames.begin(), usernames.end(), username)!= usernames.end())
	{
		cout<< "failure"<<endl; return;
	}
	else
	{
		user1->name = username;
		usernames.push_back(username);
	}
	users.push_back(user1);
}
// eventts
void addevent(vector <string> eve)
{
	evnt* event1 = new evnt;
	int start = stoi(eve[1]);
	int duration = stoi(eve[2]);
	int end = start + duration -1;
	int nums = stoi(eve[3]);
	string days = eve[0];
	int dlen = days.length();
	string date = "";
	for(int i = 0; i< dlen; i++)
	{
		if(days[i] != "-") date+=days[i];
	}
	int d;
	int u;
	int date1 = stoi(date);
	for(int i = 4; i < nums+4; i++)
	{
		if(find(usernames.begin(), usernames.end(), eve[i])
		!=usernames.end()) 
		u = find(usernames.begin(), usernames.end(), eve[i]);
		user* user1= users[u];

		if(find(user1->dates.begin(), user1->dates.end(), date1)!= user1->dates.end())
		{
		d = find(user1->dates.begin(), user1->dates.end(), date1); 
		}
		else
		{
				d = user1->dates.size();
				user1->dates.push_back(date1);
		}

		for(auto p: user1->calendar[d])
		{
			int st = p.first;
			int en = p.second;
			if(start> st && start <en) {
				cout<< "failure"<<endl; return;
			} 
			if(end > st && end <en) 
			{
 				cout<< "failure"<<endl; return;
			}
		}
		user1->calendar[d].push_back(make_pair(start, end));
		user1->parting[d].push_back(event1);
		event1->parts.push_back(user1);
	}
	cout<< "success"<<endl;
}

void showeve(string day, string user)
{
	string date = "";
	int dlen = day.length();
	if(find(usernames.begin(), usernames.end(), eve[i])
		!=usernames.end()) 
		u = find(usernames.begin(), usernames.end(), eve[i]);
		user* user1= users[u];
	for(int i = 0; i<dlen; i++)
	{
		if(day[i] != "-") date+=day[i];
	}
	int date1 = stoi(date);
	int d;
	if(find(user1->dates.begin(), user1->dates.end(), date1)!= user1->dates.end())
	{
		d = find(user1->dates.begin(), user1->dates.end(), date1); 
	}
	else
	{
		cout <<"none"<<endl; 
		return;
	}
	for(int i = 0;  i < user1->calendar[d].size(); i++)
	{
		evnt * event1 = parting[d][i];
		pair p = calendar[d][i];
		cout << p.first <<"-"<< p.second;
		for(auto u: event1->parts) cout << " " << u->name;
	}
}

void suggestslot(vector<string> slots)
{
	string day = slots[0];
	string date = "";
	for(int i = 0; i< day.length(); i++)
	{
		if(s[i] != "-") date+=s[i];
	}
	int date1 = stoi(date);
	int d;
	int start = stoi(slots[1]);
	int slot = start;
	int end = stoi(slots[2]);
	int duration = stoi(slots[3]);
	int slotend = slot + duration;
	int users = stoi(slots[4]);
	for(int i=5; i<users+5; i++)
	{
		int u;
		if(find(usernames.begin(), usernames.end(), slots[i])
		!=usernames.end()) 
		 u = find(usernames.begin(), usernames.end(), slots[i]);
		user* user1= users[u];

		if(find(user1->dates.begin(), user1->dates.end(), date1)!= user1->dates.end())
		{
		d = find(user1->dates.begin(), user1->dates.end(), date1); 
		}
		else
		{
				slot = start;
				break;
		}
		int time = slot;
		for(auto p: user1->calendar[d])
		{
			int st = p.first;
			int en = p.end;
			if(slot <st && end < st) break;
			if(slot > st && slot <en) {
				time = en;
				break;
			}
			if(slotend > st && slotend <en){
				time = en;
				break;
			}
			if(time > end) cout<< "none";
		}
	}
	cout << slot<< endl;
}
int main() {
	int num;
	cin >> num;
	while(num--)
	{
		string str;
		getline(cin, str);
		stringstream ss(str);
		vector <string> words;
		string word;
		while(ss >> word)
		{
			words.push_back(word);
			word.clear();
		}
		if(words[0]== "add-user")
		{
			// vector<string> use;
			// for(int i =1; i < words.size() ; i++)
			// {
			// 	use.push_back(words[i]);
			// }
			string use = words[1];
			adduser(use);
			use.clear();
		}
		else if(words[0]== "create-event")
		{
			vector<string> eve;
			for(int i =1; i <(int) words.size() ; i++)
			{
				eve.push_back(words[i]);
			}
			addevent(eve);
			eve.clear();
		}
		else if(words[0]== "show-events")
		{
			showeve(words[1], words[2]);
		}
		else if(words[0]== "suggest-slot")
		{
			vector<string>slots;
			for(int i =1; i <(int) words.size() ; i++)
			{
				slots.push_back(words[i]);
			}
			suggestslot(slots);
			slots.clear();
		}
	}	
}
