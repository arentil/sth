#include <iostream>
#include <time.h>
#include <stdlib.h>
using namespace std;

class TicTacToe
{
private:
	char tab[3][3];	
	char round;
	int count;
	int win;
	bool nomore;
public:
	TicTacToe();
	void mark(const int i, const int j,char v);		//zaznacza fale lub true w wierszu tab[i][j]
	void show();
	int ifwin() { return win; }
	char whosround();
	bool no_more();
};


int main()
{
	TicTacToe play;
	play.show();
	int i, j;
	while (play.ifwin() != 9)
	{
		cout << "i: ";
		cin >> i;
		cout << "j: ";
		cin >> j;
		play.mark(i, j, play.whosround());
		play.show();
		if (play.ifwin() == 1)
			break;
		else if (play.ifwin() == -1 && play.no_more() == false)
		{
			cout << "REMIS!" << endl;
			break;
		}
	}


	cin.get();
	cin.get();
	return 0;
}

bool  TicTacToe::no_more()
{
	return nomore;
}


char TicTacToe::whosround()
{
	return round;
}

TicTacToe::TicTacToe()
{
	nomore = false;
	count = 0;
	win = 0;
	char a = 'a';
	for (int i = 0; i < 3; i++)
	{
		for (int j = 0; j < 3; j++, a++)
		{
			tab[i][j] = a;
		}
	}

	srand(time(NULL));
	int dice_roll = rand() % 2 + 1;
	if (dice_roll == 1)
	{
		round = 'o';
		cout << "Zaczyna kolko!" << endl;
	}
	else if (dice_roll == 2)
	{
		round = 'x';
		cout << "Zaczyna krzyzyk!" << endl;
	}
}

void TicTacToe::mark(const int i, const int j, char v)
{
	if (tab[i][j] == 'o' || tab[i][j] == 'x')
	{
		cout << "Nie mozesz nadpisac wartosci na danym polu!" << endl;
		return;
	}
	if (round == v)
	{
		tab[i][j] = v;
		count++;
		if (round == 'x')
			round = 'o';
		else
			round = 'x';
	}
	else
	{
		cout << "Nie twoja tura!" << endl;
		return;
	}
	if ((tab[0][0] == tab[0][1] && tab[0][1] == tab[0][2]) ||
		(tab[1][0] == tab[1][1] && tab[1][1] == tab[1][2]) ||
		(tab[2][0] == tab[2][1] && tab[2][1] == tab[2][2]) ||	//w poziomie
		(tab[0][0] == tab[1][0] && tab[1][0] == tab[2][0]) ||
		(tab[0][1] == tab[1][1] && tab[1][1] == tab[2][1]) ||
		(tab[0][2] == tab[1][2] && tab[1][2] == tab[2][2]) ||	//w pionie
		(tab[0][0] == tab[1][1] && tab[1][1] == tab[2][2]) ||
		(tab[0][2] == tab[1][1] && tab[1][1] == tab[2][0]))		//po skosach
	{
		cout << "Wygral";
		nomore = true;
		if (round == 'x')
			cout << " kolko!" << endl;
		else if (round == 'o')
			cout << " krzyzyk!" << endl;
		win = 1;
	}
	if (count == 9)
		win = -1;
}

void TicTacToe::show()
{
	cout << endl;
	for (int i = 0; i < 3; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			if (tab[i][j] != 'o' && tab[i][j] != 'x')
			{
				cout << " ";
			}
			else
			{
				cout << tab[i][j];
			}
			if (j != 2)
				cout << " | ";
		}
		cout << endl;
		if (i != 2)
			cout << "--+---+--" << endl;
	}
	cout << endl;
}
