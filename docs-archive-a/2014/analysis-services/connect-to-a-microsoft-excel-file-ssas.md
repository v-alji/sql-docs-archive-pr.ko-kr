---
title: Microsoft Excel 파일에 연결 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79bb3d57470be8acbbb990dde71cf21b62b3cb2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648017"
---
# <a name="connect-to-a-microsoft-excel-file-ssas"></a><span data-ttu-id="eb439-102">Microsoft Excel 파일에 연결(SSAS)</span><span class="sxs-lookup"><span data-stu-id="eb439-102">Connect to a Microsoft Excel File (SSAS)</span></span>
  <span data-ttu-id="eb439-103">**테이블 가져오기 마법사** 의 이 페이지에서는 로컬 컴퓨터에 저장되어 있는 Microsoft Excel 파일에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-103">This page of the **Table Import Wizard** enables you to connect to a Microsoft Excel file stored on the local machine.</span></span> <span data-ttu-id="eb439-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="eb439-105">Microsoft Excel 파일에 연결하려면 컴퓨터에 적절한 ACE 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-105">To connect to a Microsoft Excel file, you must have the appropriate ACE provider installed on your computer.</span></span> <span data-ttu-id="eb439-106">자세한 내용은 [지원되는 데이터 원본&#40;SSAS 테이블 형식&#41;](tabular-models/data-sources-supported-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eb439-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb439-107">이 페이지에서 파일을 선택하는 경우 현재 사용자의 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="eb439-108">하지만 가장 정보 페이지에 지정된 사용자에게 선택한 파일을 읽을 수 있는 권한이 없는 경우에는 가져오기 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="eb439-109">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="eb439-109">UI element list</span></span>  
 <span data-ttu-id="eb439-110">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="eb439-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="eb439-111">이 데이터 원본 연결의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="eb439-112">이 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-112">This is a required field.</span></span>  
  
 <span data-ttu-id="eb439-113">**Excel 파일 경로**</span><span class="sxs-lookup"><span data-stu-id="eb439-113">**Excel File Path**</span></span>  
 <span data-ttu-id="eb439-114">Excel 파일의 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-114">Specify a full path for the Excel file.</span></span>  
  
 <span data-ttu-id="eb439-115">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="eb439-115">**Browse**</span></span>  
 <span data-ttu-id="eb439-116">Excel 파일을 사용할 수 있는 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-116">Navigate to a location where an Excel file is available.</span></span>  
  
 <span data-ttu-id="eb439-117">**고급**</span><span class="sxs-lookup"><span data-stu-id="eb439-117">**Advanced**</span></span>  
 <span data-ttu-id="eb439-118">**고급 속성 설정** 대화 상자를 사용 하 여 추가 연결 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-118">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="eb439-119">**첫 행을 열 머리글로 사용**</span><span class="sxs-lookup"><span data-stu-id="eb439-119">**Use first row as column headers**</span></span>  
 <span data-ttu-id="eb439-120">첫 번째 데이터 행을 대상 테이블의 열 머리글로 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-120">Specify whether to use the first data row as the column headers of the destination table.</span></span>  
  
 <span data-ttu-id="eb439-121">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="eb439-121">**Test Connection**</span></span>  
 <span data-ttu-id="eb439-122">현재 설정을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-122">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="eb439-123">연결이 성공적인지 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb439-123">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
