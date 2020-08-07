---
title: '작업 1: 마스터 데이터 관리자을 사용 하 여 공급자 모델 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6bbbcbff-1ecd-456c-947f-c445c8da673c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f6823c96acb7db77a3daafa895f3353b70af44dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731231"
---
# <a name="task-1-creating-suppliers-model-using-master-data-manager"></a><span data-ttu-id="76f59-102">태스크 1: 마스터 데이터 관리자를 사용하여 공급자 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="76f59-102">Task 1: Creating Suppliers Model using Master Data Manager</span></span>
  <span data-ttu-id="76f59-103">이 태스크에서는 **마스터 데이터 관리자**를 사용 하 여 MDS에서 **Suppliers** 라는 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76f59-103">In this task, you create a model named **Suppliers** in MDS using **Master Data Manager**.</span></span>  
  
1.  <span data-ttu-id="76f59-104">로 이동 `http://localhost/MDS` 하 여 **마스터 데이터 관리자**를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="76f59-104">Navigate to `http://localhost/MDS` to launch **Master Data Manager**.</span></span> <span data-ttu-id="76f59-105">웹 애플리케이션을 다른 이름으로 구성했거나 다른 웹 사이트에 구성한 경우 URL을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="76f59-105">Replace the URL if you have configured Web Application with a different name or on a different a web site.</span></span>  
  
     <span data-ttu-id="76f59-106">![시스템 데이터 관리자 - 시스템 관리](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-01.jpg "시스템 데이터 관리자 - 시스템 관리")</span><span class="sxs-lookup"><span data-stu-id="76f59-106">![Master Data Manager - System Administation](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-01.jpg "Master Data Manager - System Administation")</span></span>  
  
2.  <span data-ttu-id="76f59-107">**관리 작업** 섹션에서 **시스템 관리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76f59-107">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="76f59-108">**모델 추가** 페이지가 표시 되지 않는 경우 메뉴 모음에서 **관리** 위로 마우스를 이동 하 **고 모델을 클릭 한**다음 모델 **추가 (+)** 도구 모음 단추를 클릭 하 여 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76f59-108">If you do not see the **Add Model** page, hover mouse over **Manage** on the menu bar, click **Models**, and then click **Add Model (+)** toolbar button to create a model.</span></span>  
  
     <span data-ttu-id="76f59-109">![관리 - 모델 메뉴](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-02.jpg "관리 - 모델 메뉴")</span><span class="sxs-lookup"><span data-stu-id="76f59-109">![Manage - Models Menu](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-02.jpg "Manage - Models Menu")</span></span>  
  
     <span data-ttu-id="76f59-110">![모델 추가 도구 모음 단추](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-03.jpg "모델 추가 도구 모음 단추")</span><span class="sxs-lookup"><span data-stu-id="76f59-110">![Add Model Toolbat Button](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-03.jpg "Add Model Toolbat Button")</span></span>  
  
4.  <span data-ttu-id="76f59-111">**모델 이름**으로 **Suppliers** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="76f59-111">Enter **Suppliers** for **Model name**.</span></span>  
  
5.  <span data-ttu-id="76f59-112">**모델 옵션과 이름이 같은 엔터티 만들기** 를 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="76f59-112">Clear **Create entity with same name as model** option.</span></span> <span data-ttu-id="76f59-113">나중에 **Excel용 MDS 추가 기능**를 사용 하 여 엔터티를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76f59-113">You will create an entity later using the **MDS Add-in for Excel**.</span></span>  
  
     <span data-ttu-id="76f59-114">![모델 추가 페이지](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-04.jpg "모델 추가 페이지")</span><span class="sxs-lookup"><span data-stu-id="76f59-114">![Add Model Page](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-04.jpg "Add Model Page")</span></span>  
  
6.  <span data-ttu-id="76f59-115">도구 모음에서 **모델 저장** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="76f59-115">Click **Save Model** button on the toolbar.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="76f59-116">다음 단계</span><span class="sxs-lookup"><span data-stu-id="76f59-116">Next Step</span></span>  
 [<span data-ttu-id="76f59-117">태스크 2: Excel용 MDS 추가 기능을 사용하여 MDS에 공급자 데이터 업로드</span><span class="sxs-lookup"><span data-stu-id="76f59-117">Task 2: Uploading Supplier Data to MDS using MDS Add-in for Excel</span></span>](../../2014/tutorials/task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel.md)  
  
  
