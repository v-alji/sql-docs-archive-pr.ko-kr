---
title: 데이터를 가져오는 방법 선택 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.choosehowtoimpdata.f1
ms.assetid: 17dc6903-c239-46aa-a3b0-6e3156accacc
author: minewiskan
ms.author: owend
ms.openlocfilehash: fba1d5801f325400b228920fffa06512f4db8de2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648697"
---
# <a name="choose-how-to-import-the-data-ssas"></a><span data-ttu-id="7b500-102">데이터를 가져오는 방법 선택(SSAS)</span><span class="sxs-lookup"><span data-stu-id="7b500-102">Choose How to Import the Data (SSAS)</span></span>
  <span data-ttu-id="7b500-103">**테이블 가져오기 마법사** 의 이 페이지에서는 선택된 데이터 원본으로부터 데이터를 가져오는 방법을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b500-103">This page of the **Table Import Wizard** enables you to choose how to import data from the selected data source.</span></span> <span data-ttu-id="7b500-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b500-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="7b500-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="7b500-105">UI element list</span></span>  
 <span data-ttu-id="7b500-106">**데이터를 가져올 테이블 및 뷰를 목록에서 선택**</span><span class="sxs-lookup"><span data-stu-id="7b500-106">**Select from a list of tables and views to choose the data to import**</span></span>  
 <span data-ttu-id="7b500-107">목록에서 데이터를 선택하여 가져오려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b500-107">Select this option if you want to import data by selecting from a list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b500-108">이 옵션은 선택된 데이터 원본이 **테이블 가져오기 마법사** 에서 지원하는 스키마 정보를 노출하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b500-108">This option is available only when the selected data source exposes schema information that the **Table Import Wizard** supports.</span></span>  
  
 <span data-ttu-id="7b500-109">**가져올 데이터를 지정할 쿼리 작성**</span><span class="sxs-lookup"><span data-stu-id="7b500-109">**Write a query to specify the data to import**</span></span>  
 <span data-ttu-id="7b500-110">SQL 쿼리를 사용하여 데이터를 가져오려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b500-110">Select this option if you want to import data by using a SQL query.</span></span> <span data-ttu-id="7b500-111">SQL 쿼리에서 가져오는 데이터를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b500-111">The SQL query can manipulate the data that is imported.</span></span> <span data-ttu-id="7b500-112">예를 들어 서로 다른 테이블의 데이터를 조인하거나 특정 조건에 맞는 행만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b500-112">For example, you could join data from different tables or select only rows that meet certain criteria.</span></span>  
  
  
