## BASIC STRUCTURE

In the project there are currently 3 notebooks:
	* Visualize: 
		A place to do some basic visualizations, right now I've only visualized missing values.
	* Undersample: 
		Notebook that undersamples the training set. Any preprocessing that needs to be done
		BEFORE the set is undersampled (like taking the mean of a query variable), is done
		here as well. This also splits the training set into a training, validation and test
		set for local testing.
	* Pipeline: 
		Loads the data from undersample, does any preprocessing we need to do, trains a model and
		evaluates it. Right now we are training with the regular training set that we got from VU,
		but testing is done using the Kaggle set (so we can test on Kaggle). This is on top of the
		local testing that we already have, and just for convenience.

		There are a couple of dataframes here:
			_train: the (undersampled) training set that was derived from the original training set
			_val: the validation set that was derived from the original training set, used to determine
			when training can stop
			_test: local test set to evaluate the model, derived from original training set
			test: original test set, used to create a submission. Using Kaggle set for now

		Note that if you do any kind of preprocessing, you should do it on all of these. Sometimes you
		might prefer to do preprocessing in undersample, as you have much more information left there.
		The problem is that undersample takes a long time to run.

## GET LAMBDAMART WORKING (Assuming you're working with Anaconda)
1. Open Anaconda prompt and run the following commands to create a new Python 3.5 environment:
		conda create -n py35 python=3.5
		activate py35
		python -m ipykernel install --user --name py35 --display-name "Python (py35)"
3. Download the code from https://github.com/jma127/pyltr/tree/master/pyltr
4. Using the same Anaconda prompt run the following command in the downloaded folder:
		python setup.py install
5. To verify whether everything works, start Jupyter notebook, see if you can create a new
   "Python (py35)" notebook, and then do "import pyltr"

## GET THE DATA
1. Download the test set from https://www.kaggle.com/c/expedia-personalized-sort/data.
2. Put it in, the data folder and call it "kaggle_test.csv"
3. Download the training and test set from VU and put it in data as well
4. Run the Undersample notebook
5. Profit