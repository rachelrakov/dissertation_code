## Pipeline for getting to workable data (pipeline from beginning, starting from fresh audio?)

Data prep:
- Start with Get_data_questions_2018
- Update segment_audio.py for your data
- Also will need extract_f0.py
- push to servers where SoX and opensmile are 
    * scp (while NOT LOGGED ON TO SERVERS) local path to location on servers
- run segment_audio
- move files around so you can run extract_f0.py
- run extract_f0.py
- pull resulting file back to local machine

- Start with match_file_build_dataframes_start_times
- Then to add_data_from_test_to_train (if needed)
- Then go to counting_things data: recount how many WH/YN questions we have, how many IPUs we have from each, re-fill in that chart in the dissertation (if needed)
- Normalize f0 by speaker mean with (speaker_normalize_f0).  No need for std normalization as well.
- Then go to get_legendres
    * This is where you set degrees for legendre polynomials
    * Final classification degree is 7 degree polynomials
- Then to get_normal_distributions (this may not be a good or useful bit of code)
    * AS OF 11/1/18, SKIP THIS STEP
- Then get_contour_visualizations_and_final_probs (this has the visualizations that shows the contours)
- Then go to classify_w/probs (soon to be version that is sklearn 0.20 compatible)
- For final classification, go to final_test_train_allfeatures.  Also compute nativeness accuracy and question accuracy