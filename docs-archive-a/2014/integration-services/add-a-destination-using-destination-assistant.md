---
title: 대상 길잡이를 사용 하 여 대상 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 747a0de0-3c2f-4d31-a692-7111fc0911d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd36828a7bab7fb33b86765f9f064b6406a17a9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647816"
---
# <a name="add-a-destination-using-destination-assistant"></a><span data-ttu-id="8c2bf-102">대상 길잡이를 사용하여 대상 추가</span><span class="sxs-lookup"><span data-stu-id="8c2bf-102">Add a Destination using Destination Assistant</span></span>
  <span data-ttu-id="8c2bf-103">이 항목에서는 대상 길잡이를 사용하여 새 대상을 추가하는 단계를 제공하며, 대상 길잡이를 SSIS 디자이너에 끌어 놓으면 나타나는 **새 대상 추가** 대화 상자에서 사용할 수 있는 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c2bf-103">This topic provides steps to add a new destination using the Destination Assistant and also lists the options that are available on the **Add New Destination** dialog, which you will see when you drag-drop the Destination Assistant to the SSIS Designer.</span></span>  
  
### <a name="to-use-destination-assistant-to-add-a-destination"></a><span data-ttu-id="8c2bf-104">대상 길잡이를 사용하여 대상을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="8c2bf-104">To use Destination Assistant to add a destination</span></span>  
  
1.  <span data-ttu-id="8c2bf-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 대상 구성 요소를 추가할 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8c2bf-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that you want to add a destination component to.</span></span>  
  
2.  <span data-ttu-id="8c2bf-106">SSIS 도구 상자에서 **데이터 흐름** 탭으로 **대상 길잡이** 구성 요소를 끌어 옵니다. **새 대상 추가** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8c2bf-106">Drag the **Destination Assistant** component from the SSIS Toolbox to the **Data Flow** tab. You should see the **Add New Destination** dialog box.</span></span> <span data-ttu-id="8c2bf-107">다음 섹션에서는 대화 상자에서 사용할 수 있는 옵션에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8c2bf-107">The next section provides you details about the options available in the dialog box.</span></span>  
  
3.  <span data-ttu-id="8c2bf-108">**유형** 목록에서 대상의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8c2bf-108">Select the type of the destination in the **Types** list.</span></span>  
  
4.  <span data-ttu-id="8c2bf-109">**연결 관리자** 목록에서 기존 연결 관리자를 선택하거나 **\<New>** 를 선택하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c2bf-109">Select an existing connection manager in the **Connection Managers** list or select **\<New>** to create a new connection manager.</span></span>  
  
5.  <span data-ttu-id="8c2bf-110">기본 연결 관리자를 선택한 경우 **확인** 을 클릭하여 **새 대상 추가** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8c2bf-110">If you select an existing connection manager, click **OK** to close the **Add New Destination** dialog box.</span></span> <span data-ttu-id="8c2bf-111">데이터 흐름에 추가된 대상 및 연결 관리자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c2bf-111">You should see the destination and connection managers added to the data flow.</span></span>  
  
6.  <span data-ttu-id="8c2bf-112">**\<New>** 를 클릭하여 새 연결 관리자를 만든 경우 연결 매개 변수를 지정할 수 있는 **연결 관리자** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8c2bf-112">If you click **\<New>** to create a new connection manager, you should see a **Connection Manager** dialog box, which lets you specify parameters for the connection.</span></span> <span data-ttu-id="8c2bf-113">새 연결 관리자 만들기 작업을 마치면 SSIS 디자이너에 대상 및 연결 관리자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c2bf-113">After you are done with creating the new connection manager, you will see the destination and the connection manager in SSIS Designer.</span></span>  
  
  
