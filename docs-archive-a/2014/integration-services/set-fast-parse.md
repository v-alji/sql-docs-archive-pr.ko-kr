---
title: 빠른 구문 분석 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6ff2c6ecd536dd5ecc34dceb358ffcf578ff3a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638905"
---
# <a name="set-fast-parse"></a><span data-ttu-id="24b4c-102">빠른 구문 분석 설정</span><span class="sxs-lookup"><span data-stu-id="24b4c-102">Set Fast Parse</span></span>
  <span data-ttu-id="24b4c-103">빠른 구문 분석을 사용하는 원본 또는 변환의 각 열에는 빠른 구문 분석 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24b4c-103">The fast parse property must be set for each column of the source or transformation that uses fast parse.</span></span> <span data-ttu-id="24b4c-104">이 속성을 설정하려면 플랫 파일 원본 및 데이터 변환의 고급 편집기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24b4c-104">To set the property, use the Advanced editor of the Flat File source and Data Conversion transformation.</span></span>  
  
### <a name="to-set-fast-parse"></a><span data-ttu-id="24b4c-105">빠른 구문 분석을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="24b4c-105">To set fast parse</span></span>  
  
1.  <span data-ttu-id="24b4c-106">플랫 파일 원본이나 데이터 변환을 마우스 오른쪽 단추로 클릭하고 **고급 편집기 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24b4c-106">Right-click the Flat File source or Data Conversion transformation, and then click **Show Advanced Editor**.</span></span>  
  
2.  <span data-ttu-id="24b4c-107">**고급 편집기** 대화 상자에서 **입/출력 속성** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24b4c-107">In the **Advanced Editor** dialog box, click the **Input and Output Properties** tab.</span></span>  
  
3.  <span data-ttu-id="24b4c-108">**입/출력** 창에서 빠른 구문 분석을 설정할 열을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24b4c-108">In the **Inputs and Outputs** pane, click the column for which you want to enable fast parse.</span></span>  
  
4.  <span data-ttu-id="24b4c-109">속성 창에서 **사용자 지정 속성** 노드를 확장 하 고 속성을로 설정 `FastParse` `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24b4c-109">In the Properties window, expand the **Custom Properties** node, and then set the `FastParse` property to `True`.</span></span>  
  
5.  <span data-ttu-id="24b4c-110">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24b4c-110">Click **OK**.</span></span>  
  
  
