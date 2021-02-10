# Trained_CNN_models_GCsand
A repository containing different trained CNN models along with naming conventions

These are keras model objects for convolutional neural networks trained on oblique images from grand canyon sandbars.
These models are used for semantic segmentation of sandbar imagery. As more imagery is labeled models are updated and re-trained
This repo houses them. 


The model types are Unet, Res-Unet, and Unet with dropout layers. These models are visible in the Unet_models.py script in this repo
When building a Res-Unet model the batch-size is required at the onset.

These models are trained on various training/testing datasets. training sets are seperated into K=5 folds and a model is trained
for each fold, then all five models are used to predict each image and their prediction masks are averaged. For more information
my other repository {}.

# Model naming conventions

Model names should be 27 characters plus an extension.
character breakdown and order shown:
Model_type(2) + Classes(2) + Optimizer(2) + Loss(2) + batch_size(2) + img_type(2) +train_set_name(5) + date(8) + fold(2) + .h5

## Model type
the type of model trained, see Unet_models.py for how they are constructed
 two-characters
model_type = {'ResUnet': 'Ru',
              'Unet' : 'Un',
              'UnetDrop' : 'Ud'}
## Seg Class
this is wheather the model was trained for binary or multi-class semantic segmentation of sand
 two-characters
seg_class = {'Binary Sand_other': 'Bs',
         'Multiclass Sand_water_other': 'M3'}
         
## Optimizer
This is the optimizer used in CNN training
two-characters

optimizers = {'Adam': 'Ad',
              'RMSprop':'Rp'}
## Loss
The loss function used during trainging and validation 
two-characters

loss_funcs = {'Dice_Loss' : 'Dl',
              'IoU' : 'IU'}
## Batch_size
This is the number of images in each training batch, this might be limited by your available RAM, we used 3 or 5.
This is important to specify for the res-unet model which requires batch-size when initiating the model, less important with the 
other two.
two-characters, its the key rather than the entry for this dictionary
batch_size_dict = {'b3' : 3,
                   'b5' : 5}
                   
## image type
sometimes rectified images were used, other times the raw oblique images were used, and sometimes a mixture

img_type = {'rect_only': 'Rt',
            'unrectified': 'Ur',
            'mixture': 'Mx'}
                   
 ## Train_set_name
 
 There were several different training sets, or sets of images used. Sometimes for testing purposes we only trained on a single site
 other times we used all available images, and other times we just used a select number of sites, this should reflect the last re-training
 five-characters
 
 
 train_sets = {'RC0307Rfonly' : '0307R',
              'RC0307Rf_RC0220Ra :'30n22',
              's22_23_30' : '3sits'
              's30_22_122_145' : '4sits',
              's22_23_30_55_145': '5sits',
              'all_or_many' : 'manys'}
              
   ## Date
   This is the date the model was last trained or re-trained
   YYYYMMDD 8 character date code
   
   ## Fold
   there will be five folds for each model, this 2-character code should signify fold number out of 5
   f1, f2, f3, f4, or f5
   
   An example model name would be:
   
   ### RuBsAdDlb3Rtmanys20210210f1.h5
   
                   
                   
               
          

