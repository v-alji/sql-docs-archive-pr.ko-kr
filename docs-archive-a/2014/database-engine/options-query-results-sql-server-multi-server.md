---
title: 옵션 (쿼리 결과-SQL Server-다중 서버) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
author: rothja
ms.author: jroth
ms.openlocfilehash: 8273ad5edc65dd7351533209e9fa670c49f75f7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736747"
---
# <a name="options-query-results-sql-server-multi-server"></a><span data-ttu-id="23d4f-102">옵션(쿼리 결과-SQL Server-다중 서버)</span><span class="sxs-lookup"><span data-stu-id="23d4f-102">Options (Query Results-SQL Server-Multi-Server)</span></span>
  <span data-ttu-id="23d4f-103">여러 서버를 동시에 쿼리할 때 이 페이지를 사용하여 결과 집합 표시 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23d4f-103">When you are querying multiple servers at the same time, use this page to specify the options for displaying result sets.</span></span> <span data-ttu-id="23d4f-104">결과를 병합하면 모든 서버의 결과 집합이 단일 결과 집합으로 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="23d4f-104">Merge results combines the result sets from all servers into a single result set.</span></span> <span data-ttu-id="23d4f-105">결과를 병합할 때 응답할 첫 번째 서버가 결과 집합에 대한 스키마를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="23d4f-105">When merging results, the first server to respond sets the schema for the result set.</span></span> <span data-ttu-id="23d4f-106">결과 집합을 병합하려면 쿼리가 각 서버에서 같은 열 이름을 사용하는 동일한 수의 열을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23d4f-106">To merge the result sets, the query must return the same number of columns with the same column names from each server.</span></span> <span data-ttu-id="23d4f-107">결과를 병합할 때는 결과를 반환할 첫 번째 서버에서 반환된 스키마(열 개수 및 열 이름)와 일치하지 않는 각 서버에 대해 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23d4f-107">When merging results, a message is displayed for each server that does not match the schema (column count and column names) that is returned by the first server to return results.</span></span>  
  
 <span data-ttu-id="23d4f-108">결과를 병합하지 않을 때는 각 서버의 결과 집합이 자체 스키마와 함께 자체 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="23d4f-108">When you do not merge results, the result set from each server will be displayed in its own grid with its own schema.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="23d4f-109">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="23d4f-109">UI element list</span></span>  
 <span data-ttu-id="23d4f-110">**결과 병합**</span><span class="sxs-lookup"><span data-stu-id="23d4f-110">**Merge results**</span></span>  
 <span data-ttu-id="23d4f-111">여러 서버의 결과 집합을 같은 표로 결합하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23d4f-111">Select this check box to combine the result sets from several servers into the same grid.</span></span>  
  
 <span data-ttu-id="23d4f-112">**결과에 서버 이름 추가**</span><span class="sxs-lookup"><span data-stu-id="23d4f-112">**Add server name to the results**</span></span>  
 <span data-ttu-id="23d4f-113">각 행을 생성한 서버의 이름을 제공하는 추가 열을 포함하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23d4f-113">Select this check box to include an additional column that provides the name of the server that produced each row.</span></span>  
  
 <span data-ttu-id="23d4f-114">**결과에 로그인 이름 추가**</span><span class="sxs-lookup"><span data-stu-id="23d4f-114">**Add login name to the results**</span></span>  
 <span data-ttu-id="23d4f-115">각 행을 제공한 서버에 연결하는 데 사용된 로그인을 제공하는 추가 열을 포함하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="23d4f-115">Select this check box to include an additional column that provides the login that was used to connect to the server that provided each row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d4f-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23d4f-116">See Also</span></span>  
 <span data-ttu-id="23d4f-117">[중앙 관리 서버 및 서버 그룹 &#40;SQL Server Management Studio를 만듭니다&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md) </span><span class="sxs-lookup"><span data-stu-id="23d4f-117">[Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md) </span></span>  
 [<span data-ttu-id="23d4f-118">여러 서버에 대해 동시에 문 실행&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="23d4f-118">Execute Statements Against Multiple Servers Simultaneously &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  
