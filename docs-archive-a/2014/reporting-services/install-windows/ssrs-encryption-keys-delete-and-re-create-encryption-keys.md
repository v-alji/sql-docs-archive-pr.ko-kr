---
title: 암호화 키 삭제 및 다시 만들기(SSRS 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- re-creating encryption keys
- encryption keys [Reporting Services]
- deleting encryption keys
- symmetric keys [Reporting Services]
- removing encryption keys
- resetting encryption keys
ms.assetid: 201afe5f-acc9-4a37-b5ec-121dc7df2a61
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8fa5138e4bbb84395bad79a272d2bde31389396b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742935"
---
# <a name="delete-and-re-create-encryption-keys--ssrs-configuration-manager"></a><span data-ttu-id="47cdf-102">암호화 키 삭제 및 다시 만들기(SSRS 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="47cdf-102">Delete and Re-create Encryption Keys  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="47cdf-103">암호화 키를 삭제했다가 다시 만드는 작업은 정기적인 암호화 키 유지 관리 작업에 해당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-103">Deleting and re-creating encryption keys are activities that fall outside of routine encryption key maintenance.</span></span> <span data-ttu-id="47cdf-104">보고서 서버가 위협을 받을 때나 보고서 서버 데이터베이스에 더 이상 액세스할 수 없을 때 마지막 수단으로 이러한 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-104">You perform these tasks in response to a specific threat to your report server, or as a last resort when you can no longer access a report server database.</span></span>  
  
-   <span data-ttu-id="47cdf-105">기존 대칭 키가 노출된 것으로 판단되면 대칭 키를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-105">Re-create the symmetric key when you believe the existing symmetric key is compromised.</span></span> <span data-ttu-id="47cdf-106">또한 보안을 향상시키기 위해 정기적으로 키를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-106">You can also re-create the key on a regular basis as a security best practice.</span></span>  
  
-   <span data-ttu-id="47cdf-107">대칭 키를 복원할 수 없는 경우 기존 암호화 키를 삭제하고 암호화된 내용을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-107">Delete existing encryption keys and unusable encrypted content when you cannot restore the symmetric key.</span></span>  
  
## <a name="re-creating-encryption-keys"></a><span data-ttu-id="47cdf-108">암호화 키 다시 만들기</span><span class="sxs-lookup"><span data-stu-id="47cdf-108">Re-creating Encryption Keys</span></span>  
 <span data-ttu-id="47cdf-109">허가되지 않은 사용자가 대칭 키를 알고 있다고 간주되거나 보고서 서버가 공격을 받고 있어 예방 차원에서 대칭 키를 다시 설정하려는 경우 대칭 키를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-109">If you have evidence that the symmetric key is known to unauthorized users, or if your report server has been under attack and you want to reset the symmetric key as a precaution, you can re-create the symmetric key.</span></span> <span data-ttu-id="47cdf-110">대칭 키를 다시 만들면 암호화된 모든 값이 새 값을 사용하여 다시 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-110">When you re-create the symmetric key, all encrypted values will be re-encrypted using the new value.</span></span> <span data-ttu-id="47cdf-111">스케일 아웃 배포에서 여러 보고서 서버를 실행할 경우 대칭 키의 모든 복사본이 새 값으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-111">If you are running multiple report servers in a scale-out deployment, all copies of the symmetric key will be updated to the new value.</span></span> <span data-ttu-id="47cdf-112">보고서 서버는 사용 가능한 공개 키를 사용하여 배포의 각 서버에 대해 해당 대칭 키를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-112">The report server uses the public keys available to it to update the symmetric key for each server in the deployment.</span></span>  
  
 <span data-ttu-id="47cdf-113">보고서 서버가 작동 상태일 때만 대칭 키를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-113">You can only re-create the symmetric key when the report server is in a working state.</span></span> <span data-ttu-id="47cdf-114">암호화 키를 다시 만들고 내용을 다시 암호화하면 서버 작동이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-114">Re-creating the encryption keys and re-encrypting content disrupts server operations.</span></span> <span data-ttu-id="47cdf-115">다시 암호화하는 동안 서버를 오프라인으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-115">You must take the server offline while re-encryption is underway.</span></span> <span data-ttu-id="47cdf-116">다시 암호화하는 동안에는 보고서 서버에 대해 요청이 수행되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-116">There should be no requests made to the report server during re-encryption.</span></span>  
  
 <span data-ttu-id="47cdf-117">Reporting Services 구성 도구나 **rskeymgmt** 유틸리티를 사용하여 대칭 키와 암호화된 데이터를 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-117">You can use the Reporting Services Configuration tool or the **rskeymgmt** utility to reset the symmetric key and encrypted data.</span></span> <span data-ttu-id="47cdf-118">대칭 키를 만드는 방법은 [보고서 서버 초기화&#40;SSRS 구성 관리자&#41;](ssrs-encryption-keys-initialize-a-report-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47cdf-118">For more information about how the symmetric key is created, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
#### <a name="how-to-re-create-encryption-keys-reporting-services-configuration-tool"></a><span data-ttu-id="47cdf-119">암호화 키를 다시 만드는 방법(Reporting Services 구성 도구)</span><span class="sxs-lookup"><span data-stu-id="47cdf-119">How to re-create encryption keys (Reporting Services Configuration Tool)</span></span>  
  
1.  <span data-ttu-id="47cdf-120">rsreportserver.config 파일에서 `IsWebServiceEnabled` 속성을 수정하여 보고서 서버 웹 서비스 및 HTTP 액세스를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-120">Disable the Report Server Web service and HTTP access by modifying the `IsWebServiceEnabled` property in the rsreportserver.config file.</span></span> <span data-ttu-id="47cdf-121">이 단계에서는 서버를 완전히 종료하지 않고 보고서 서버로 보내는 인증 요청을 임시로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-121">This step temporarily stops authentication requests from being sent to the report server without completely shutting down the server.</span></span> <span data-ttu-id="47cdf-122">키를 다시 만들 수 있는 최소한의 서비스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-122">You must have minimal service so that you can recreate the keys.</span></span>  
  
     <span data-ttu-id="47cdf-123">보고서 서버 스케일 아웃 배포를 위해 암호화 키를 다시 만들 경우 배포의 모든 인스턴스에서 이 속성을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-123">If you are recreating encryption keys for a report server scale-out deployment, disable this property on all instances in the deployment.</span></span>  
  
    1.  <span data-ttu-id="47cdf-124">Windows 탐색기를 열고 *drive*:\Program Files\Microsoft SQL Server\\*report_server_instance*\Reporting Services로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-124">Open Windows Explorer and navigate to *drive*:\Program Files\Microsoft SQL Server\\*report_server_instance*\Reporting Services.</span></span> <span data-ttu-id="47cdf-125">여기서 *drive* 는 드라이브 문자이고 *report_server_instance* 는 웹 서비스 및 HTTP 액세스를 사용하지 않도록 설정할 보고서 서버 인스턴스에 해당하는 폴더 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-125">Replace *drive* with your drive letter and *report_server_instance* with the folder name that corresponds to the report server instance for which you want to disable the Web service and HTTP access.</span></span> <span data-ttu-id="47cdf-126">예를 들면 C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-126">For example, C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services.</span></span>  
  
    2.  <span data-ttu-id="47cdf-127">rsreportserver.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-127">Open the rsreportserver.config file.</span></span>  
  
    3.  <span data-ttu-id="47cdf-128">`IsWebServiceEnabled` 속성에 `False`를 지정한 다음 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-128">For the `IsWebServiceEnabled` property, specify `False`, and then save your changes.</span></span>  
  
2.  <span data-ttu-id="47cdf-129">Reporting Services 구성 도구를 시작한 후 구성하려는 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-129">Start the Reporting Services Configuration tool, and then connect to the report server instance you want to configure.</span></span>  
  
3.  <span data-ttu-id="47cdf-130">암호화 키 페이지에서 **변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-130">On the Encryption Keys page, click **Change**.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="47cdf-131">보고서 서버 Windows 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-131">Restart the Report Server Windows service.</span></span> <span data-ttu-id="47cdf-132">스케일 아웃 배포를 위해 암호화 키를 다시 만들 경우 모든 인스턴스에서 해당 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-132">If you are recreating encryption keys for a scale-out deployment, restart the service on all instances.</span></span>  
  
5.  <span data-ttu-id="47cdf-133">rsreportserver.config 파일에서 `IsWebServiceEnabled` 속성을 수정하여 보고서 서비스 및 HTTP 액세스를 다시 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-133">Re-enable the Web service and HTTP access by modifying the `IsWebServiceEnabled` property in the rsreportserver.config file.</span></span> <span data-ttu-id="47cdf-134">확장 배포 구성에서 작업할 경우에는 모든 인스턴스에 대해 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-134">Do this for all instances if you are working with a scale out deployment.</span></span>  
  
#### <a name="how-to-re-create-encryption-keys-rskeymgmt"></a><span data-ttu-id="47cdf-135">암호화 키를 다시 만드는 방법(rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="47cdf-135">How to re-create encryption keys (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="47cdf-136">보고서 서버 웹 서비스 및 HTTP 액세스를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-136">Disable the Report Server Web service and HTTP access.</span></span> <span data-ttu-id="47cdf-137">이전 절차의 지시대로 웹 서비스 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-137">Use the instructions in the previous procedure to stop Web service operations.</span></span>  
  
2.  <span data-ttu-id="47cdf-138">보고서 서버를 호스팅하는 컴퓨터에서 **rskeymgmt.exe** 를 로컬로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-138">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="47cdf-139">`-s` 인수를 사용하여 대칭 키를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-139">Use the `-s` argument to reset the symmetric key.</span></span> <span data-ttu-id="47cdf-140">다른 인수는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-140">No other arguments are required:</span></span>  
  
    ```  
    rskeymgmt -s  
    ```  
  
3.  <span data-ttu-id="47cdf-141">Windows 서비스를 다시 시작하고 웹 서비스 작업을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-141">Restart the Windows service and enable Web service operations.</span></span>  
  
## <a name="deleting-unusable-encrypted-content"></a><span data-ttu-id="47cdf-142">사용할 수 없는 암호화된 내용 삭제</span><span class="sxs-lookup"><span data-stu-id="47cdf-142">Deleting Unusable Encrypted Content</span></span>  
 <span data-ttu-id="47cdf-143">여타의 이유로 암호화 키를 복원할 수 없는 경우 보고서 서버는 암호를 해독할 수 없으며 해당 키로 암호화된 어떠한 데이터도 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-143">If for some reason you cannot restore the encryption key, the report server will never be able to decrypt and use any data that is encrypted with that key.</span></span> <span data-ttu-id="47cdf-144">보고서 서버를 작동 상태로 되돌리려면 보고서 서버 데이터베이스에 현재 저장되어 있는 암호화된 값을 삭제한 후 필요한 값을 수동으로 다시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-144">To return the report server to a working state, you must delete the encrypted values that are currently stored in the report server database and then manually re-specify the values you need.</span></span>  
  
 <span data-ttu-id="47cdf-145">암호화 키를 삭제하면 보고서 서버 데이터베이스에서 모든 대칭 키 정보가 제거되고 암호화된 모든 내용이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-145">Deleting the encryption keys removes all symmetric key information from the report server database and deletes any encrypted content.</span></span> <span data-ttu-id="47cdf-146">암호화되지 않은 데이터는 모두 그대로 남아 있으며 암호화된 내용만 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-146">All unencrypted data is left intact; only encrypted content is removed.</span></span> <span data-ttu-id="47cdf-147">암호화 키를 삭제하면 보고서 서버는 새 대칭 키를 추가하여 자체적으로 다시 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-147">When you delete the encryption keys, the report server re-initializes itself automatically by adding a new symmetric key.</span></span> <span data-ttu-id="47cdf-148">암호화된 내용을 삭제하면 다음 상황이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-148">The following occurs when you delete encrypted content:</span></span>  
  
-   <span data-ttu-id="47cdf-149">공유 데이터 원본의 연결 문자열이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-149">Connection strings in shared data sources are deleted.</span></span> <span data-ttu-id="47cdf-150">보고서를 실행하면 "ConnectionString 속성이 초기화되지 않았습니다"라는 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-150">Users who run reports get the error "The ConnectionString property has not been initialized."</span></span>  
  
-   <span data-ttu-id="47cdf-151">저장된 자격 증명이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-151">Stored credentials are deleted.</span></span> <span data-ttu-id="47cdf-152">프롬프트된 자격 증명을 사용하도록 보고서 및 공유 데이터 원본이 다시 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-152">Reports and shared data sources are reconfigured to use prompted credentials.</span></span>  
  
-   <span data-ttu-id="47cdf-153">모델을 기반으로 하며 저장된 자격 증명을 사용하여 구성되거나 자격 증명 없이 구성된 공유 데이터 원본을 요구하는 보고서는 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-153">Reports that are based on models (and require shared data sources configured with stored or no credentials) will not run.</span></span>  
  
-   <span data-ttu-id="47cdf-154">구독이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-154">Subscriptions are deactivated.</span></span>  
  
 <span data-ttu-id="47cdf-155">암호화된 내용을 삭제한 경우 다시 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-155">Once you delete encrypted content, you cannot recover it.</span></span> <span data-ttu-id="47cdf-156">연결 문자열과 저장된 자격 증명을 다시 지정하고 구독을 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-156">You must re-specify connection strings and stored credentials, and you must activate subscriptions.</span></span>  
  
 <span data-ttu-id="47cdf-157">Reporting Services 구성 도구나 **rskeymgmt** 유틸리티를 사용하여 값을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-157">You can use the Reporting Services Configuration tool or the **rskeymgmt** utility to remove the values.</span></span>  
  
#### <a name="how-to-delete-encryption-keys-reporting-services-configuration-tool"></a><span data-ttu-id="47cdf-158">암호화 키를 삭제하는 방법(Reporting Services 구성 도구)</span><span class="sxs-lookup"><span data-stu-id="47cdf-158">How to delete encryption keys (Reporting Services Configuration Tool)</span></span>  
  
1.  <span data-ttu-id="47cdf-159">Reporting Services 구성 도구를 시작한 후 구성하려는 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-159">Start the Reporting Services Configuration tool, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="47cdf-160">**암호화 키**를 클릭한 후 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-160">Click **Encryption Keys**, and then click **Delete**.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="47cdf-161">보고서 서버 Windows 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-161">Restart the Report Server Windows service.</span></span> <span data-ttu-id="47cdf-162">스케일 아웃 배포의 경우 모든 보고서 서버 인스턴스에 대해 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-162">For a scale-out deployment, do this on all report server instances.</span></span>  
  
#### <a name="how-to-delete-encryption-keys-rskeymmgt"></a><span data-ttu-id="47cdf-163">암호화 키를 삭제하는 방법(rskeymmgt)</span><span class="sxs-lookup"><span data-stu-id="47cdf-163">How to delete encryption keys (rskeymmgt)</span></span>  
  
1.  <span data-ttu-id="47cdf-164">보고서 서버를 호스팅하는 컴퓨터에서 **rskeymgmt.exe** 를 로컬로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-164">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="47cdf-165">**-d** 적용 인수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-165">You must use the **-d** apply argument.</span></span> <span data-ttu-id="47cdf-166">다음은 인수 지정 예입니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-166">The following example illustrates the argument you must specify:</span></span>  
  
    ```  
    rskeymgmt -d  
    ```  
  
2.  <span data-ttu-id="47cdf-167">보고서 서버 Windows 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-167">Restart the Report Server Windows service.</span></span> <span data-ttu-id="47cdf-168">스케일 아웃 배포의 경우 모든 보고서 서버 인스턴스에 대해 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-168">For a scale-out deployment, do this on all report server instances.</span></span>  
  
#### <a name="how-to-re-specify-encrypted-values"></a><span data-ttu-id="47cdf-169">암호화된 값을 다시 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="47cdf-169">How to re-specify encrypted values</span></span>  
  
1.  <span data-ttu-id="47cdf-170">각 공유 데이터 원본에 대해 연결 문자열을 다시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-170">For each shared data source, you must retype the connection string.</span></span>  
  
2.  <span data-ttu-id="47cdf-171">저장된 자격 증명을 사용하는 각 보고서 및 공유 데이터 원본의 경우 사용자 이름과 암호를 다시 입력한 후 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-171">For each report and shared data source that uses stored credentials, you must retype the user name and password, and then save.</span></span> <span data-ttu-id="47cdf-172">자세한 내용은 [온라인 설명서에서](../../integration-services/connection-manager/data-sources.md) 보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47cdf-172">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
3.  <span data-ttu-id="47cdf-173">각 데이터 기반 구독에 대해 각 구독을 열고 구독 데이터베이스에 대한 자격 증명을 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-173">For each data-driven subscription, open each subscription and retype the credentials to the subscription database.</span></span>  
  
4.  <span data-ttu-id="47cdf-174">암호화된 데이터(파일 공유 배달 확장 프로그램과 암호화를 사용하는 타사의 배달 확장 프로그램 포함)를 사용하는 구독의 경우 각 구독을 열고 자격 증명을 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-174">For subscriptions that use encrypted data (this includes the File Share delivery extension and any third-party delivery extension that uses encryption), open each subscription and retype credentials.</span></span> <span data-ttu-id="47cdf-175">보고서 서버 전자 메일 배달을 사용하는 구독은 암호화된 데이터를 사용하지 않으므로 키가 달라져도 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47cdf-175">Subscriptions that use Report Server e-mail delivery do not use encrypted data and are unaffected by the key change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47cdf-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47cdf-176">See Also</span></span>  
 <span data-ttu-id="47cdf-177">[SSRS Configuration Manager &#40;암호화 키 구성 및 관리&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="47cdf-177">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="47cdf-178">암호화된 보고서 서버 데이터 저장&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="47cdf-178">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  
