---
title: OLE 자동화 결과 집합 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- data types [SQL Server], OLE Automation
- two-dimensional arrays
- one-dimensional arrays
- result sets [SQL Server], OLE Automation
- OLE Automation [SQL Server], result sets
- arrays [SQL Server]
ms.assetid: b2f99e33-2303-427c-94b9-9d55f8e2a6ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7c9bdc4d51d989db2d4d676b29e0824c0e5b59a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661631"
---
# <a name="ole-automation-result-sets"></a><span data-ttu-id="734f9-102">OLE 자동화 결과 집합</span><span class="sxs-lookup"><span data-stu-id="734f9-102">OLE Automation Result Sets</span></span>
  <span data-ttu-id="734f9-103">OLE 자동화 속성 또는 메서드에서 1차원 또는 2차원 배열로 데이터를 반환하면 해당 배열은 클라이언트에 결과 집합으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-103">If an OLE Automation property or method returns data in an array with one or two dimensions, the array is returned to the client as a result set:</span></span>  
  
-   <span data-ttu-id="734f9-104">1차원 배열은 배열 내 요소 수만큼의 열이 포함된 단일 행 결과 집합으로 클라이언트에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-104">A one-dimensional array is returned to the client as a single-row result set with as many columns as there are elements in the array.</span></span> <span data-ttu-id="734f9-105">예를 들어 array(10)는 10개의 열이 포함된 단일 행으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-105">For example, an array(10) is returned as a single row of 10 columns.</span></span>  
  
-   <span data-ttu-id="734f9-106">2차원 배열은 배열의 첫 번째 차원에 있는 요소 수만큼의 열과 두 번째 차원에 있는 요소 수만큼의 행이 포함된 결과 집합으로 클라이언트에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-106">A two-dimensional array is returned to the client as a result set with as many columns as there are elements in the first dimension of the array and with as many rows as there are elements in the second dimension of the array.</span></span> <span data-ttu-id="734f9-107">예를 들어 array(2,3)는 2개의 열과 3개의 행으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-107">For example, an array(2,3) is returned as 2 columns in 3 rows.</span></span>  
  
 <span data-ttu-id="734f9-108">속성 반환 값이나 메서드 반환 값이 배열인 경우 sp_OAGetProperty나 sp_OAMethod가 결과 집합을 클라이언트에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-108">When a property return value or method return value is an array, sp_OAGetProperty or sp_OAMethod returns a result set to the client.</span></span> <span data-ttu-id="734f9-109">(메서드 출력 매개 변수는 배열이 될 수 없습니다) 이러한 프로시저는 배열의 모든 데이터 값을 검색하여 결과 집합의 각 열에 알맞은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식과 데이터 길이를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-109">(Method output parameters cannot be arrays.) These procedures scan all the data values in the array to determine the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and data lengths to use for each column in the result set.</span></span> <span data-ttu-id="734f9-110">특정 열에 대해서는 이러한 프로시저에서 해당 열의 모든 데이터 값을 나타내기 위해 필요한 데이터 형식과 길이를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-110">For a particular column, these procedures use the data type and length required to represent all data values in that column.</span></span>  
  
 <span data-ttu-id="734f9-111">하나의 열에 있는 모든 데이터 값이 같은 데이터 형식을 공유하는 경우에는 해당 데이터 형식이 전체 열에 대해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-111">When all data values in a column share the same data type, that data type is used for the whole column.</span></span> <span data-ttu-id="734f9-112">한 열의 여러 데이터 값이 다른 데이터 형식을 사용하는 경우에는 다음 표를 기준으로 전체 열의 데이터 형식이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-112">When data values in a column are different data types, the data type of the whole column is chosen based on the following table.</span></span> <span data-ttu-id="734f9-113">다음 표를 사용하려면 왼쪽 행 축에 나열된 데이터 형식 중 하나를 찾은 다음 두 번째 데이터 형식으로 위쪽 열 축에 나열된 데이터 형식을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-113">To use the following table, find one data type along the left row axis and a second data type along the top column axis.</span></span> <span data-ttu-id="734f9-114">행과 열이 교차하는 위치에 결과 집합 열의 데이터 형식이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="734f9-114">The intersection of the row and column describes the data type of the result set column.</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
||`int`|`float`|`money`|`datetime`|`varchar`|`nvarchar`|  
|`int`|`int`|`float`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`float`|`float`|`float`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`money`|`money`|`money`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`datetime`|`varchar`|`varchar`|`varchar`|`datetime`|`varchar`|`nvarchar`|  
|`varchar`|`varchar`|`varchar`|`varchar`|`varchar`|`varchar`|`nvarchar`|  
|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|  
  
## <a name="related-content"></a><span data-ttu-id="734f9-115">관련 내용</span><span class="sxs-lookup"><span data-stu-id="734f9-115">Related Content</span></span>  
 [<span data-ttu-id="734f9-116">OLE 자동화 저장 프로시저&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="734f9-116">OLE Automation Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql)  
  
 [<span data-ttu-id="734f9-117">Ole Automation Procedures 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="734f9-117">Ole Automation Procedures Server Configuration Option</span></span>](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
  
