---
title: 데이터 흐름 경로 편집기에서 경로 메타 데이터 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Integration Services]
- paths [Integration Services], metadata
ms.assetid: 25cf8bdd-8691-4caa-96b6-3081b2f37dea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d84e14c2bc42ac4b831a4d1a3321d3e8b4acf6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638892"
---
# <a name="view-path-metadata-in-the-data-flow-path-editor"></a><span data-ttu-id="da406-102">데이터 흐름 경로 편집기를 사용하여 경로 메타데이터 보기</span><span class="sxs-lookup"><span data-stu-id="da406-102">View Path Metadata in the Data Flow Path Editor</span></span>
  <span data-ttu-id="da406-103">경로는 두 개의 데이터 흐름 구성 요소를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="da406-103">Paths connect two data flow components.</span></span> <span data-ttu-id="da406-104">경로 메타데이터를 보려면 데이터 흐름에 적어도 두 개 이상의 연결된 데이터 흐름 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da406-104">Before you can view path metadata, the data flow must contain at least two connected data flow components.</span></span> <span data-ttu-id="da406-105">자세한 내용은 [데이터 흐름에서 구성 요소 추가 또는 삭제](data-flow/add-or-delete-a-component-in-a-data-flow.md) 및 [데이터 흐름의 구성 요소 연결](data-flow/connect-components-in-a-data-flow.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da406-105">For more information, see [Add or Delete a Component in a Data Flow](data-flow/add-or-delete-a-component-in-a-data-flow.md) and [Connect Components in a Data Flow](data-flow/connect-components-in-a-data-flow.md).</span></span>  
  
### <a name="to-view-path-metadata"></a><span data-ttu-id="da406-106">경로 메타데이터를 보려면</span><span class="sxs-lookup"><span data-stu-id="da406-106">To view path metadata</span></span>  
  
1.  <span data-ttu-id="da406-107">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="da406-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="da406-108">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="da406-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="da406-109">**데이터 흐름** 탭을 클릭하고 경로를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da406-109">Click the **Data Flow** tab and double-click a path.</span></span>  
  
4.  <span data-ttu-id="da406-110">**데이터 흐름 경로 편집기** 대화 상자에서 **메타데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da406-110">In **Data Flow Path Editor** dialog box, click **Metadata**.</span></span>  
  
5.  <span data-ttu-id="da406-111">열 이름, 데이터 형식, 전체 자릿수, 소수 자릿수, 길이, 코드 페이지 및 각 열에 대한 원본 구성 요소의 이름과 같은 경로 메타데이터를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="da406-111">View path metadata, including the column names, data type, precision, scale, length, code page, and the name of the source component of each column.</span></span>  
  
6.  <span data-ttu-id="da406-112">메타데이터를 복사하려면 **클립보드로 복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da406-112">To copy the metadata, click **Copy to Clipboard**.</span></span>  
  
7.  <span data-ttu-id="da406-113">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da406-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da406-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da406-114">See Also</span></span>  
 <span data-ttu-id="da406-115">[Integration Services 경로](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="da406-115">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="da406-116">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="da406-116">Data Flow</span></span>](data-flow/data-flow.md)  
  
  
