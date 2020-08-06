---
title: 연결 문자열 지정 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.speconnstring.f1
ms.assetid: 3f89b55b-2659-4e9f-a3ad-ab9a23b6942d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9333c239504a79184e08776acb3f1d845f06cc4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736855"
---
# <a name="specify-a-connection-string-ssas"></a><span data-ttu-id="3821e-102">연결 문자열 지정(SSAS)</span><span class="sxs-lookup"><span data-stu-id="3821e-102">Specify a connection string (SSAS)</span></span>
  <span data-ttu-id="3821e-103">**테이블 가져오기 마법사** 의 이 페이지에서는 OLE DB 또는 ODBC 데이터 원본에 연결하기 위한 연결 문자열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3821e-103">This page of the **Table Import Wizard** enables you to specify a connection string to connect to an OLE DB or ODBC data source.</span></span> <span data-ttu-id="3821e-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3821e-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="3821e-105">데이터 원본에 연결하려면 컴퓨터에 적절한 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3821e-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span> <span data-ttu-id="3821e-106">지원되는 데이터 원본 및 공급자에 대한 자세한 내용은 [지원되는 데이터 원본&#40;SSAS 테이블 형식&#41;](tabular-models/data-sources-supported-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3821e-106">For more information about supported data sources and providers, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="3821e-107">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="3821e-107">UI element list</span></span>  
 <span data-ttu-id="3821e-108">**이 연결 이름**</span><span class="sxs-lookup"><span data-stu-id="3821e-108">**Friendly name for this connection**</span></span>  
 <span data-ttu-id="3821e-109">이 데이터 원본 연결의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3821e-109">Type a unique name for this data source connection.</span></span> <span data-ttu-id="3821e-110">이 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3821e-110">This is a required field.</span></span>  
  
 <span data-ttu-id="3821e-111">**연결 문자열**</span><span class="sxs-lookup"><span data-stu-id="3821e-111">**Connection String**</span></span>  
 <span data-ttu-id="3821e-112">OLE DB 또는 ODBC 데이터 원본에 연결하기 위한 연결 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3821e-112">Type a connection string to connect to an OLE DB or ODBC data source.</span></span>  
  
 <span data-ttu-id="3821e-113">**빌드**</span><span class="sxs-lookup"><span data-stu-id="3821e-113">**Build**</span></span>  
 <span data-ttu-id="3821e-114">**데이터 연결 속성** 대화 상자를 사용하여 연결 문자열의 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3821e-114">Specify the properties for a connection string by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="3821e-115">자세한 내용은 이 대화 상자에서 Microsoft 데이터 연결 도움말을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3821e-115">For more information, see the Microsoft Data Link Help, which is available from that dialog box.</span></span>  
  
 <span data-ttu-id="3821e-116">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="3821e-116">**Test Connection**</span></span>  
 <span data-ttu-id="3821e-117">지정한 연결 문자열을 사용하여 데이터 원본에 대한 연결을 설정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3821e-117">Attempt to establish a connection to the data source using the specified connection string.</span></span> <span data-ttu-id="3821e-118">연결이 성공적인지 여부를 나타내는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3821e-118">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
