---
title: 유사 항목 그룹화 변환 편집기 (연결 관리자 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2a8b0af9f36fdd386f7da375184fd4e4ec5c4be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659529"
---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a><span data-ttu-id="1ead0-102">유사 항목 그룹화 변환 편집기(연결 관리자 탭)</span><span class="sxs-lookup"><span data-stu-id="1ead0-102">Fuzzy Grouping Transformation Editor (Connection Manager Tab)</span></span>
  <span data-ttu-id="1ead0-103">**유사 항목 그룹화 변환 편집기** 대화 상자의 **연결 관리자** 탭을 사용하여 기존 연결을 선택하거나 새 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ead0-103">Use the **Connection Manager** tab of the **Fuzzy Grouping Transformation Editor** dialog box to select an existing connection or create a new one.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ead0-104">연결에 지정된 서버에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ead0-104">The server specified by the connection must be running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ead0-105">유사 항목 그룹화 변환에서는 변환에 대한 전체 입력만큼 클 수 있는 임시 데이터 개체를 tempdb에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ead0-105">The Fuzzy Grouping transformation creates temporary data objects in tempdb that may be as large as the full input to the transformation.</span></span> <span data-ttu-id="1ead0-106">실행되는 동안 변환에서는 이러한 임시 개체에 대한 서버 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1ead0-106">While the transformation executes, it issues server queries against these temporary objects.</span></span> <span data-ttu-id="1ead0-107">이 작업은 전체적인 서버 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ead0-107">This can affect overall server performance.</span></span>  
  
 <span data-ttu-id="1ead0-108">유사 항목 그룹화 변환에 대한 자세한 내용은 [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ead0-108">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1ead0-109">옵션</span><span class="sxs-lookup"><span data-stu-id="1ead0-109">Options</span></span>  
 <span data-ttu-id="1ead0-110">**캐시 없음**</span><span class="sxs-lookup"><span data-stu-id="1ead0-110">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="1ead0-111">목록 상자를 사용하여 기존 OLE DB 연결 관리자를 선택하거나 **새로 만들기** 단추를 사용하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ead0-111">Select an existing OLE DB connection manager by using the list box, or create a new connection by using the **New** button.</span></span>  
  
 <span data-ttu-id="1ead0-112">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="1ead0-112">**New**</span></span>  
 <span data-ttu-id="1ead0-113">**OLE DB 연결 관리자 구성** 대화 상자를 사용하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ead0-113">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ead0-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ead0-114">See Also</span></span>  
 <span data-ttu-id="1ead0-115">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1ead0-115">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="1ead0-116">유사 항목 그룹화 변환을 사용하여 유사한 데이터 행 식별</span><span class="sxs-lookup"><span data-stu-id="1ead0-116">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
