# encoding: utf-8
# MEHDI SAMENI
# ver 0.0.1
# Date and Time : jalali 09/08/95 _ 15:15:15
'''
___Match Shape with opencv and python ___

opencv __version__ : 3.1.0
python __version__ : 2.7.11

im1 = is input image reference
im2 = is input image new

'''

im1 = cv2.imread('img10.jpg')
im2 = cv2.imread('img5.jpg')

img1 = cv2.cvtColor(im1, cv2.COLOR_BGR2GRAY)
img2 = cv2.cvtColor(im2, cv2.COLOR_BGR2GRAY)

ret, thresh = cv2.threshold(img1, 127, 255, 0)
ret, thresh2 = cv2.threshold(img2, 127, 255, 0)

_,contours, hierarchy = cv2.findContours(thresh, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
cnt1 = contours[0]

_,contours, hierarchy = cv2.findContours(thresh2, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
cnt2 = contours[0]

hull = cv2.convexHull(cnt1, returnPoints=False)
defects = cv2.convexityDefects(cnt1, hull)
for i in range(defects.shape[0]):
    s, e, f, d = defects[i, 0]
    start = tuple(cnt1[s][0])
    end = tuple(cnt1[e][0])
    far = tuple(cnt1[f][0])
    cv2.line(im1, start, end, [0, 255, 0], 2)
    cv2.circle(im1, far, 5, [0, 0, 255], -1)


hull = cv2.convexHull(cnt2, returnPoints=False)
defects = cv2.convexityDefects(cnt2, hull)
for i in range(defects.shape[0]):
    s, e, f, d = defects[i, 0]
    start = tuple(cnt2[s][0])
    end = tuple(cnt2[e][0])
    far = tuple(cnt2[f][0])
    cv2.line(im2, start, end, [0, 255, 0], 2)
    cv2.circle(im2, far, 5, [0, 0, 255], -1)

cv2.imshow('img1',im1)
cv2.imshow('img2',im2)
cv2.waitKey(0)

ret = cv2.matchShapes(cnt1, cnt2, 1, 0.0)
print ret
