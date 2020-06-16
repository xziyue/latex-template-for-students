# Beautiful LaTeX templates for students

Examples can be seen in [test_titlepage.pdf](./test_titlepage.pdf).

## Beautiful title page

- Source: `my-titlepage.sty`

- Usage

  ```latex
  \makecustomtitle{lotus}
  
  % use "nourl" option to suppress project url
  \makecustomtitle[nourl]{lotus}
  ```

- Available templates:  `brushes`, `checkbox`, `dots`, `koi`, `lotus`

- These artworks are acquired from [GoodNotes](https://www.goodnotes.com/), please ask for their permission for commercial use!

- Changing layout

  The macro `\mtp_declare_new_style:n` is used to define new layouts. The definitions created for each macro are (`#1` is the name of template):

  ```latex
  \dim_new:c {g_#1_title_x_dim} % title x offset
  \dim_new:c {g_#1_title_y_dim} % title y offset
  \dim_new:c {g_#1_title_width_dim} % title width
  \dim_new:c {g_#1_ad_x_dim} % author date x offset
  \dim_new:c {g_#1_ad_y_dim} % author date y offset
  \dim_new:c {g_#1_ad_width_dim} % author date width
  \tl_new:c {g_#1_title_font_tl} % title font
  \tl_new:c {g_#1_ad_font_tl} % author date font
  ```

  For example, if one wants to change the title color of `lotus` to red as well as the width of title to `10cm`, then the following code should be added before calling `\makecustomtitle`:

  ```latex
  \ExplSyntaxOn
  \tl_gset:cn {g_lotus_title_font_tl} {\fontsize{42}{30}\color{red}\scshape}
  \dim_gset:cn {g_lotus_title_width_dim} {10cm}
  \ExplSyntaxOff
  ```

  

## Beautiful Disclosure Sheet

- Source: `my-disclosure-sheet.sty`

- Usage

  ```latex
  % if one wants to provide details, put them in this environment
  % this environment must precede \makedisclosuresheet
  \begin{disclosuredetail}
          hello
          \begin{itemize}
              \item I talked with A.
              \item I copied B.
          \end{itemize}
  \end{disclosuredetail}
  
  \makedisclosuresheet{
          consultothers, % use this option to toggle first claim
          outsidesource, % use this option to toggle second claim
          course={CIS-375 (Spring 2020)}, % course name
          docid={HM 4}, % document ID
          author={Ziyue ``Alan'' Xiang} % author name
   }
  ```

- If one does not specify `author`, then the `name` field will use the value of `\@author` by default. However, problems will occur when `\and` command is present. In this case, please specify `author` manually.

