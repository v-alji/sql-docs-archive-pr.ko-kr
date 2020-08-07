---
title: CDC 인스턴스 속성을 보는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4bce9b82-7bbd-41df-b3f4-4b40b8bad474
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86fa298b0e02a16ddbaea220ef7f3d9f6172bf85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732880"
---
# <a name="how-to-view-the-cdc-instance-properties"></a><span data-ttu-id="da741-102">CDC 인스턴스 속성을 보는 방법</span><span class="sxs-lookup"><span data-stu-id="da741-102">How to View the CDC Instance Properties</span></span>
  <span data-ttu-id="da741-103">이 절차에서는 CDC Designer 콘솔을 사용하여 인스턴스 작업을 쉽게 관리하기 위해 만든 인스턴스에 대한 정보를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="da741-103">This procedure describes how to use the CDC Designer Console to view information about the instances that you create to help manage the operation of the instances.</span></span>  
  
### <a name="to-view-information-about-a-specific-instance"></a><span data-ttu-id="da741-104">특정 인스턴스에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="da741-104">To view information about a specific instance</span></span>  
  
1.  <span data-ttu-id="da741-105">**시작** 메뉴에서 **CDC Designer 콘솔**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da741-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="da741-106">왼쪽 창에서 **변경 데이터 캡처** 를 확장한 다음 보려는 인스턴스를 포함하는 서비스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="da741-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance you want to view.</span></span>  
  
3.  <span data-ttu-id="da741-107">작업할 인스턴스의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da741-107">Select the name of an instance you want to work with.</span></span>  
  
     <span data-ttu-id="da741-108">인스턴스에 대한 정보는 CDC Designer 콘솔의 가운데 부분에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da741-108">The information about the instance is displayed in the center part of the CDC Designer Console.</span></span> <span data-ttu-id="da741-109">또한 4개의 탭으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="da741-109">It is divided into four tabs.</span></span> <span data-ttu-id="da741-110">모든 탭은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="da741-110">All of the tabs are read only.</span></span>  
  
     <span data-ttu-id="da741-111">**상태**</span><span class="sxs-lookup"><span data-stu-id="da741-111">**Status**</span></span>  
     <span data-ttu-id="da741-112">이 탭에는 인스턴스에 대한 변경 데이터 캡처의 현재 상태에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da741-112">This tab displays the information about the current status of the change data capture for the instance.</span></span> <span data-ttu-id="da741-113">이 탭에 표시되는 내용에 대한 자세한 내용은 **Manage a CDC Instance** 에서 [뷰어 탭](manage-a-cdc-instance.md)섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="da741-113">For information about what is displayed in this tab, see the **Viewer Tabs** section in [Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
     <span data-ttu-id="da741-114">**Oracle**</span><span class="sxs-lookup"><span data-stu-id="da741-114">**Oracle**</span></span>  
     <span data-ttu-id="da741-115">이 탭에는 CDC 인스턴스 및 Oracle 원본 데이터베이스에 대한 일반 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da741-115">This tab displays general information about the CDC instance and the Oracle source database.</span></span> <span data-ttu-id="da741-116">이 탭에 표시되는 내용에 대한 자세한 내용은 [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="da741-116">For information about what is displayed in this tab, see [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).</span></span>  
  
     <span data-ttu-id="da741-117">**테이블**</span><span class="sxs-lookup"><span data-stu-id="da741-117">**Tables**</span></span>  
     <span data-ttu-id="da741-118">이 탭에는 변경 데이터 캡처에 포함된 테이블에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da741-118">This tab displays information about the tables included in the change data capture.</span></span> <span data-ttu-id="da741-119">또한 캡처되는 열이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="da741-119">It also lists the columns that are captured.</span></span> <span data-ttu-id="da741-120">이 탭에 표시되는 내용에 대한 자세한 내용은 [Edit Tables](edit-tables.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="da741-120">For information about what is displayed in this tab, see [Edit Tables](edit-tables.md).</span></span>  
  
     <span data-ttu-id="da741-121">**고급**</span><span class="sxs-lookup"><span data-stu-id="da741-121">**Advanced**</span></span>  
     <span data-ttu-id="da741-122">이 탭에는 속성 편집기에서 정의하는 고급 속성 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da741-122">This tab displays a list of advanced properties that you define in the properties editor.</span></span> <span data-ttu-id="da741-123">이 탭에 표시되는 내용에 대한 자세한 내용은 [Edit the Advanced Properties](edit-the-advanced-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="da741-123">For information about what is displayed in this tab, see [Edit the Advanced Properties](edit-the-advanced-properties.md).</span></span>  
  
  
