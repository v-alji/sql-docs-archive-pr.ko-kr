---
title: Azure Storage 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpstorageconn.f1
- sql11.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 47580d8d1d961df9fbcbed0bd7164f1c54792b86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651225"
---
# <a name="azure-storage-connection-manager"></a><span data-ttu-id="e9696-102">Azure Storage 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e9696-102">Azure Storage Connection Manager</span></span>
  <span data-ttu-id="e9696-103">SSIS 패키지는 Azure Storage 연결 관리자를 통해 속성으로 지정된 값(스토리지 계정 이름 및 계정 키)을 사용하여 Azure Storage 계정에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9696-103">The Azure Storage connection manager enables an SSIS package to connect to an Azure Storage account by using the values you specify for the properties: Storage Account Name and Account Key.</span></span>  
  
1.  <span data-ttu-id="e9696-104">**SSIS 연결 관리자 추가** 대화 상자에서 **AzureStorage**를 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9696-104">In the **Add SSIS Connection Manager** dialog box, select **AzureStorage**, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="e9696-105">Azure Storage 연결 관리자 편집기 대화 상자에서 **Azure 계정 사용**을 선택하여 인터넷을 통해 Azure Storage 서비스에 연결하거나 **로컬 개발자 계정 사용**을 선택하여 Azure Storage 에뮬레이터가 호스트하는 로컬 서비스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e9696-105">In the Azure Storage Connection Manager Editor dialog box, choose **Use Azure account** to connect to an Azure Storage Service via internet or choose **Use local developer account** to connect to the local service hosted by the Azure Storage Emulator.</span></span>  
  
3.  <span data-ttu-id="e9696-106">**Azure 계정 사용** 옵션을 선택하는 경우 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e9696-106">If you selected **Use Azure account** option, do the following:</span></span>  
  
    1.  <span data-ttu-id="e9696-107">**스토리지 계정 이름** 및 **계정 키** 필드의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e9696-107">Specify values for the **Storage account name** and **Account key** field.</span></span> <span data-ttu-id="e9696-108">이러한 값은 SSIS 패키지에 중요한 데이터로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e9696-108">These values will be stored as sensitive data in SSIS package.</span></span>  
  
    2.  <span data-ttu-id="e9696-109">HTTP 대신 HTTPS를 사용하여 Azure Storage 서비스에 연결하려면 **HTTPS 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9696-109">Select **Use HTTPS** if you want to use HTTPS instead of HTTP to connect to the Azure Storage Service.</span></span>  
  
4.  <span data-ttu-id="e9696-110">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e9696-110">Click **OK** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="e9696-111">작성한 연결 관리자의 속성은 **속성** 창에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9696-111">You can see the properties of the connection manager you created in the **Properties** window.</span></span>  
  
  
