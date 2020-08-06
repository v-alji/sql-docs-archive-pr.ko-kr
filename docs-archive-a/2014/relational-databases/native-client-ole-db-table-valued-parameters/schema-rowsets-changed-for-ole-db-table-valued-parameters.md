---
title: OLE DB 테이블 반환 매개 변수에 대해 변경된 스키마 행 집합 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
author: rothja
ms.author: jroth
ms.openlocfilehash: e09d5127f332c8b6cc948be3eeb74e600bb856f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739796"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a><span data-ttu-id="62adb-102">OLE DB 테이블 반환 매개 변수에 대해 변경된 스키마 행 집합</span><span class="sxs-lookup"><span data-stu-id="62adb-102">Schema Rowsets Changed for OLE DB Table-Valued Parameters</span></span>
  <span data-ttu-id="62adb-103">다음은 테이블 반환 매개 변수를 지원하기 위해 변경 또는 추가된 스키마 행 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-103">The following are the schema rowsets that have been changed or added to support table-valued parameters.</span></span>  
  
|<span data-ttu-id="62adb-104">스키마 행 집합</span><span class="sxs-lookup"><span data-stu-id="62adb-104">Schema rowset</span></span>|<span data-ttu-id="62adb-105">설명</span><span class="sxs-lookup"><span data-stu-id="62adb-105">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="62adb-106">DBSCHEMA_PROCEDURE_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="62adb-106">DBSCHEMA_PROCEDURE_PARAMETERS</span></span>|<span data-ttu-id="62adb-107">SS_TYPE_CATALOG_NAME 및 SS_TYPE_SCHEMANAME이라는 두 개의 새 열이 행 집합 끝에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-107">Two new columns were added at the end of the rowset named SS_TYPE_CATALOG_NAME and SS_TYPE_SCHEMANAME.</span></span> <span data-ttu-id="62adb-108">두 열은 이후 유형에 다시 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-108">These columns could be re-used for future types.</span></span> <span data-ttu-id="62adb-109">TYPE_NAME 및 LOCAL_TYPE_NAME 열에는 테이블 반환 매개 변수 TABLE 유형의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-109">The TYPE_NAME and LOCAL_TYPE_NAME columns will contain the name of the table-valued parameter TABLE type.</span></span> <span data-ttu-id="62adb-110">테이블 반환 매개 변수의 경우 DATA_TYPE 열에 값 DBTYPE_TABLE = 143이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-110">The DATA_TYPE column will have value DBTYPE_TABLE = 143 for table-valued parameters.</span></span>|  
|<span data-ttu-id="62adb-111">DBSCHEMA_TABLE_TYPES</span><span class="sxs-lookup"><span data-stu-id="62adb-111">DBSCHEMA_TABLE_TYPES</span></span>|<span data-ttu-id="62adb-112">이 행 집합은 테이블 반환 매개 변수를 지원하기 위해 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-112">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="62adb-113">테이블 유형에 대해서만 메타데이터를 반환하고 테이블, 뷰 또는 동의어에 대해서는 반환하지 않는다는 점을 제외하고 DBSCHEMA_TABLES와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-113">It is identical to DBSCHEMA_TABLES, except that it returns metadata only for table types, rather than for tables, views, or synonyms.</span></span> <span data-ttu-id="62adb-114">TABLE_TYPE 열은 값 'TABLE TYPE'을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-114">The TABLE_TYPE column will have the value 'TABLE TYPE'.</span></span>|  
|<span data-ttu-id="62adb-115">DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS</span><span class="sxs-lookup"><span data-stu-id="62adb-115">DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS</span></span>|<span data-ttu-id="62adb-116">이 행 집합은 테이블 반환 매개 변수를 지원하기 위해 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-116">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="62adb-117">테이블 유형에 대해서만 기본 키 메타데이터를 반환하고 테이블에 대해서는 반환하지 않는다는 점을 제외하고 DBSCHEMA_PRIMARY_KEYS와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-117">It is identical to DBSCHEMA_PRIMARY_KEYS, except that it returns primary keys metadata only for table types, rather than for tables.</span></span>|  
|<span data-ttu-id="62adb-118">DBSCHEMA_TABLE_TYPE_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="62adb-118">DBSCHEMA_TABLE_TYPE_COLUMNS</span></span>|<span data-ttu-id="62adb-119">이 행 집합은 테이블 반환 매개 변수를 지원하기 위해 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-119">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="62adb-120">테이블 유형에 대해서만 열 메타데이터를 반환하고 테이블, 뷰 또는 동의어에 대해서는 반환하지 않는다는 점을 제외하고 DBSCHEMA_COLUMNS와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="62adb-120">It is identical to DBSCHEMA_COLUMNS, except that it returns column metadata only for table types, rather than for tables, views, or synonyms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62adb-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62adb-121">See Also</span></span>  
 <span data-ttu-id="62adb-122">[테이블 반환 매개 변수 OLE DB &#40;&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="62adb-122">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="62adb-123">테이블 반환 매개 변수&#40;OLE DB&#41; 사용</span><span class="sxs-lookup"><span data-stu-id="62adb-123">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
