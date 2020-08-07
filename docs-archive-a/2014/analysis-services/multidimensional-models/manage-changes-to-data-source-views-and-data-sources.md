---
title: 데이터 원본 뷰 및 데이터 원본에 대 한 변경 내용 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data sources
- modifying data source views
- data source views [Analysis Services], schema updates
- data sources [Analysis Services], schema updates
ms.assetid: 928c9f63-365a-43fd-9bbd-78828cc7e54d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f558ce6aaf9e57576d5773322352d33b81a3392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730968"
---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a><span data-ttu-id="444df-102">데이터 원본 뷰 및 데이터 원본에 대한 변경 내용 관리</span><span class="sxs-lookup"><span data-stu-id="444df-102">Manage Changes to Data Source Views and Data Sources</span></span>
  <span data-ttu-id="444df-103">스키마 생성 마법사는 다시 실행될 때 원래 생성에 사용한 것과 동일한 데이터 원본 및 데이터 원본 뷰를 다시 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="444df-103">When the Schema Generation Wizard is rerun, it reuses the same data source and data source view that it used for the original generation.</span></span> <span data-ttu-id="444df-104">사용자가 추가하는 데이터 원본이나 데이터 원본 뷰는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="444df-104">If you add a data source or a data source view, the wizard does not use it.</span></span> <span data-ttu-id="444df-105">처음 생성 후 원래 데이터 원본이나 데이터 원본 뷰를 삭제하는 경우에는 마법사를 처음부터 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="444df-105">If you delete the original data source or data source view after the initial generation, you must run the wizard from the beginning.</span></span> <span data-ttu-id="444df-106">마법사의 이전 설정도 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="444df-106">All previous settings in the wizard are also deleted.</span></span> <span data-ttu-id="444df-107">삭제된 데이터 원본이나 데이터 원본 뷰에 바인딩된 기본 데이터베이스의 기존 개체는 다음에 스키마 생성 마법사를 실행할 때 사용자가 만든 개체로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="444df-107">Any existing objects in an underlying database that were bound to a deleted data source or data source view are treated as user-created objects the next time you run the Schema Generation Wizard.</span></span>  
  
 <span data-ttu-id="444df-108">생성 시 데이터 원본 뷰에 기본 데이터베이스의 실제 상태가 반영되지 않으면 스키마 생성 마법사가 주제 영역 데이터베이스에 대한 스키마를 생성할 때 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="444df-108">If the data source view does not reflect the actual state of the underlying database at the time of generation, the Schema Generation Wizard may encounter errors when it generates the schema for the subject area database.</span></span> <span data-ttu-id="444df-109">예를 들어 데이터 원본 뷰에서 열 데이터 형식을 **int**로 지정하지만 열 데이터 형식이 실제로 **string**인 경우 스키마 생성 마법사는 데이터 원본 뷰에 일치하도록 외래 키 데이터 형식을 **INT** 로 설정하면 실제 형식이 **string**이기 때문에 관계를 만들 때 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="444df-109">For example, if the data source view specifies that the data type for a column is **int**, but data type for the column is actually **string**, the Schema Generation Wizard sets the data type for the foreign key to **INT** to match the data source view and then fails when it creates the relationship because the actual type is **string**.</span></span>  
  
 <span data-ttu-id="444df-110">반면, 데이터 원본 연결 문자열을 이전 생성에서 다른 데이터베이스로 변경하는 경우에는 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="444df-110">On the other hand, if you change the data source connection string to a different database from the previous generation, no error is generated.</span></span> <span data-ttu-id="444df-111">새 데이터베이스가 사용되고 이전 데이터베이스는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="444df-111">The new database is used, and no change is made to the previous database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444df-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="444df-112">See Also</span></span>  
 [<span data-ttu-id="444df-113">증분 생성 이해</span><span class="sxs-lookup"><span data-stu-id="444df-113">Understanding Incremental Generation</span></span>](understanding-incremental-generation.md)  
  
  
