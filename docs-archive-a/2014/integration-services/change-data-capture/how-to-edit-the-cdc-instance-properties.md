---
title: CDC 인스턴스 속성을 편집하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7a6c719a-3735-43b7-b3ab-dfadd325eca2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b02785a32fa1f64d5da0c3202acd7916da1e65ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728608"
---
# <a name="how-to-edit-the-cdc-instance-properties"></a><span data-ttu-id="98ec0-102">CDC 인스턴스 속성을 편집하는 방법</span><span class="sxs-lookup"><span data-stu-id="98ec0-102">How to Edit the CDC Instance Properties</span></span>
  <span data-ttu-id="98ec0-103">이 절차에서는 CDC Designer 콘솔을 사용하여 CDC 인스턴스에 대한 구성 속성을 편집하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-103">This procedure describes how to use the CDC Designer Console to edit the configuration properties for a CDC instance.</span></span>  
  
### <a name="to-edit-the-cdc-instance-configuration-properties"></a><span data-ttu-id="98ec0-104">CDC 인스턴스 구성 속성을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="98ec0-104">To edit the CDC instance configuration properties</span></span>  
  
1.  <span data-ttu-id="98ec0-105">**시작** 메뉴에서 **CDC Designer 콘솔**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="98ec0-106">왼쪽 창에서 **변경 데이터 캡처** 를 확장한 다음 편집할 속성을 가진 인스턴스를 포함하는 서비스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance with the properties that you want to edit.</span></span>  
  
3.  <span data-ttu-id="98ec0-107">속성을 편집할 인스턴스의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-107">Select the name of the instance where you want to edit the properties.</span></span>  
  
4.  <span data-ttu-id="98ec0-108">CDC Designer 콘솔의 오른쪽에 있는 동작 창에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-108">From the Actions pane on the right side of the CDC Designer Console, click **Properties**.</span></span>  
  
     <span data-ttu-id="98ec0-109">속성을 편집할 인스턴스를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-109">You can also right-click the instance where you want to edit the properties and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="98ec0-110">속성 편집기의 다음 탭에서 속성을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-110">In the Properties editor, edit the properties in the following tabs:</span></span>  
  
    -   <span data-ttu-id="98ec0-111">**Oracle**: U속성 편집기에서 **Oracle** 탭을 사용하여 새 인스턴스 마법사의 CDC 데이터베이스 만들기 페이지에 제공한 설명을 변경하고 Oracle 로그 마이닝 데이터베이스 연결 정보를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-111">**Oracle**: Use the **Oracle** tab in the Properties editor to make changes to the description you provided in the Create CDC database page in the New Instance wizard and to make changes to the Oracle Log Mining database connection information.</span></span>  
  
         <span data-ttu-id="98ec0-112">이 탭에서 편집할 수 있는 항목에 대한 자세한 내용은 [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="98ec0-112">For information about what you can edit in this tab, see [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).</span></span>  
  
    -   <span data-ttu-id="98ec0-113">**테이블**: **테이블** 탭을 사용하여 Oracle 원본 데이터베이스에서 선택한 테이블과 열을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-113">**Tables**: Use the **Tables** tab to make changes to the tables and columns that you selected from the Oracle source database.</span></span>  
  
         <span data-ttu-id="98ec0-114">이 탭에서 편집할 수 있는 항목에 대한 자세한 내용은 [Edit Tables](edit-tables.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="98ec0-114">For information about what you can edit in this tab, see Edit [Edit Tables](edit-tables.md)</span></span>  
  
    -   <span data-ttu-id="98ec0-115">**스크립트**: **스크립트** 탭을 사용하여 보완 로깅을 설정할 Oracle 원본 데이터베이스에서 스크립트를 실행하거나 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-115">**Scripts**: Use the **Scripts** tab to run or re-run a script on the Oracle source database that will set up supplemental logging.</span></span>  
  
         <span data-ttu-id="98ec0-116">이 탭에서 수행할 수 있는 작업에 대한 자세한 내용은 [Review and Generate Supplemental Logging Scripts](review-and-generate-supplemental-logging-scripts.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="98ec0-116">For information about what you can do in this tab, see [Review and Generate Supplemental Logging Scripts](review-and-generate-supplemental-logging-scripts.md).</span></span>  
  
    -   <span data-ttu-id="98ec0-117">**고급**: **고급** 탭을 사용하여 CDC 인스턴스에 특별 속성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98ec0-117">**Advanced**: Use the **Advanced** tab to add special properties to the CDC instance.</span></span>  
  
         <span data-ttu-id="98ec0-118">이 탭에서 수행할 수 있는 작업에 대한 자세한 내용은 [Edit the Advanced Properties](edit-the-advanced-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="98ec0-118">For information about what you can do in this tab, see [Edit the Advanced Properties](edit-the-advanced-properties.md).</span></span>  
  
  
