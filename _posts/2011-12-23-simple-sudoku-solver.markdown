---
layout: post
title: Simple Sudoku-Solver
date: 2011-12-23 12:29:26.000000000 +01:00
---
I've always wanted to program a sudoku solver. It's a funny little problem which is essentially a computation with a little logic mixed in. There are <a href="http://en.wikipedia.org/wiki/Algorithmics_of_sudoku" title=wikipedia">many ways</a> to solve a sudoku. Some of the more involved are constraint programming and stochastic search. 

![Entered Sudoku](/images/Screen-Shot-2011-12-23-at-11.17.34.png)

There are actually approaches that just fill the numbers brute force. So they start with e.g. 1 in the first cell and then try 1 again in the next cell. Because it was already used they advance the counter to 2 and go on. If none of the 9 numbers works for a cell they go back one cell and increase its counter by one. Surprisingly this approach is actually viable, although there 6.67 x 10^21 different possible grids.

![Solved Sudoku](/images/Screen-Shot-2011-12-23-at-11.17.52.png)

As a middle way, I've implemented a backtracking solution that at least takes into account the rules for rows, columns and 3x3-squares. I haven't optimized the program for speed and it can take a couple of seconds for the harder sudokus.


The main magic happens in the recursiveSolve() method:
{% highlight cpp %}
bool Solver::recursiveSolve(int depth)
{
    if( checkFilled() ) {
        return true;
    }

    QList<Decision> decisions;

    bool addedDerivations;
    do {
        addedDerivations=false;
        if( !checkValid(addedDerivations, decisions) ) {
            reverseDecisions( decisions );
            return false;
        }
    } while( addedDerivations );

    if( checkFilled() ) {
        return true;
    }

    int r=0; // row
    int c=0; // column
    bool found_empty_cell=false;
    for(int i=0;i<ENTRIES && !found_empty_cell; i++ ) {
        for(int j=0;j<ENTRIES; j++ ) {
            if( used_numbers[i][j]==0 ) {
                r = i;
                c = j;
                found_empty_cell = true;
                break;
            }
        }
    }

    if( !found_empty_cell ) {
        reverseDecisions( decisions );
        return false;
    } else {
        QSet<int> numbers_to_try_cell( numbers_to_try[r][c] );
        for( QSet<int>::const_iterator const_it=numbers_to_try_cell.begin(); const_it!=numbers_to_try_cell.end(); const_it++) {
            Decision candidate(r,c,*const_it);
            decisions.push_back(candidate);
            used_numbers[r][c]=*const_it;
            if( recursiveSolve(depth+1) ) {
                return true;
            } else {
                // removing try
                used_numbers[r][c]=0;
                decisions.pop_back();
            }
        }
    }

    // backtracking to higher recursion level
    reverseDecisions( decisions );
    return false;
}
{% endhighlight %}

First the program tries to derive all the numbers that follow logically from existing numbers. These "derivations" are then stored as are the different choices that are tried in each backtracking step. If a backtracking step turns out to be invalid it returns false and its calling step tries another value for the cell in question.

You can download the whole thing <a href='/assets/SudokuSolver_0.1.zip'>here</a>. It's a Qt project that you can easily import into Qt Creator that's part of <a href="http://qt.nokia.com/products/qt-sdk/" title="Qt-SDK">Qt-SDK</a>.
